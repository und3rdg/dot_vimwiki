tested on archaic system:
- gulp 3.9
- node 8.4


    var gulp = require('gulp')
    var sourcemaps = require('gulp-sourcemaps')
    var concat = require('gulp-concat')
    var sass = require('gulp-sass')
    var cleanCSS = require('gulp-clean-css')
    var plumber = require('gulp-plumber')
    var autoprefixer = require('gulp-autoprefixer')
    var uglify = require('gulp-uglify-es').default
    var babel = require('gulp-babel')
    var buffer = require('vinyl-buffer')
    var source = require('vinyl-source-stream')
    var browserify = require('browserify')
    var babelify = require('babelify')

    const css = {
        in: 'sass/index.scss',
        dir: '../dist/css/',
        out : 'bundle.css',
    }
    const es5 = {
        in: 'js/regular/*.js',
        out: 'bundle.js',
        dir: '../dist/js'
    }
    const es6 = {
        in: './js/index.js',
        out: 'modular-bundle.js',
        dir: '../dist/js/'
    }

    const is_dev  = process.argv[2] === "watch"
    const is_prod = !is_dev

    console.log(`
    ==================
        ${is_dev
        ? 'developing' 
        : 'production'}
    ==================
    `)


    gulp.task('scss', function () {
        let STREAM = gulp.src(css.in).pipe(plumber())
        STREAM = is_dev
            ? STREAM.pipe(sourcemaps.init())
            : STREAM
        STREAM = STREAM.pipe(sass().on('error', sass.logError))
            .pipe(autoprefixer())
            .pipe(concat(css.out))
            .pipe(cleanCSS({ compatibility: 'ie11' }))
        STREAM = is_dev
            ? STREAM.pipe(sourcemaps.write('./'))
            : STREAM
            
        return STREAM.pipe(gulp.dest(css.dir))
    })



    function js_es5() {
        const cfg_babel ={
            presets: ['@babel/env']
        } 

        let STREAM = gulp.src(es5.in).pipe(plumber())
        STREAM = is_dev
            ? STREAM.pipe(sourcemaps.init())
            : STREAM
        STREAM = STREAM.pipe(concat(es5.out))
            .pipe(babel(cfg_babel))
        STREAM = is_prod
            ? STREAM.pipe(uglify())
            : STREAM
        STREAM = is_dev
            ? STREAM.pipe(sourcemaps.write('./'))
            : STREAM
            
        return STREAM.pipe(gulp.dest(es5.dir))
    }


    gulp.task('javascript', () => {
        const cfg = {
            browserify: { entries: es6.in, debug: false },
            transform: {
                    presets: ['@babel/env', '@babel/react'],
                    plugins: ['@babel/plugin-proposal-class-properties'],
                    sourceMaps: is_dev,
                }
        }

        let STREAM = browserify(cfg.browserify)
            .transform(
                babelify, cfg.transform)
            .bundle().on('error', function(err) {
                console.log(err.toString())
                this.emit('end')
            })
            .pipe(plumber())
            .pipe(source(es6.out))
            .pipe(buffer())
        STREAM = is_dev
            ? STREAM.pipe(sourcemaps.init({ loadMaps: true }))
            : STREAM
        STREAM = is_prod
            ? STREAM.pipe(uglify())
            : STREAM
        STREAM = is_dev
            ? STREAM.pipe(sourcemaps.write('./'))
            : STREAM

        js_es5()
        return STREAM.pipe(gulp.dest(es6.dir))
    })





    /*
      |------------|------------------------------------|
      | command    | description                        |
      |------------|------------------------------------|
      | gulp       | Run this BEFORE EVERY COMMIT!!!!!! |
      |            | it will compile css and js.        |
      |            | it will DO exit after first run.   |
      |------------|------------------------------------|
      | gulp watch | This is for developing process     |
      |            | it will compile css and js.        |
      |            | it will NOT exit after first run.  |
      |------------|------------------------------------|
      */



    gulp.task('watch', ['scss', 'javascript'], function () {
        gulp.watch('./sass/**/*', ['scss'])
        gulp.watch('./js/**/*', ['javascript'])
    })


    gulp.task('default', ['scss', 'javascript'])


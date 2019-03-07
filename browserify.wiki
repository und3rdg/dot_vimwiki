## browserify in gulp

    const gulp         = require('gulp')
    const sourcemaps   = require('gulp-sourcemaps')
        //sourcemaps compatibility ->
        //https://github.com/gulp-sourcemaps/gulp-sourcemaps/wiki/Plugins-with-gulp-sourcemaps-support
    const browserify   = require('browserify')
    const babelify     = require('babelify')
    const source       = require('vinyl-source-stream')
    const buffer       = require('vinyl-buffer')
    const uglify       = require('gulp-uglify')


    const jsEs6 = () => {
        const browserify_settings = {
            entries: 'es6_source_folder/index.js', 
            debug: true,
        }

        return browserify(browserify_settings)
            .transform(babelify.configure({ presets: [ '@babel/env' ], }))
            .bundle().on('error', err => console.error(err.message))
            .pipe(source('output_file_name.js'))
            .pipe(buffer())
        // browserify end, back in gulp

            .pipe(sourcemaps.init({loadMaps: true}))
            .pipe(uglify())
            .pipe(sourcemaps.write('./'))
            .pipe(gulp.dest('dist/destination/folder'))
    }

    //////////////////////////////////////////////
    // GULP TASK
    gulp.task('js', ()=>{
        jsEs6()
    })
    // GULP TASK
    //////////////////////////////////////////////





## async alternative for BrowserSync

    const bsync = require('browser-sync').create()

    gulp.task('browserSync', () => {
        bsync.init({
            /* usual browser sync server setup
            (...) 
            */
        })
    })


    gulp.task('js', ()=>{
        jsEs6().on('end', bsync.reload) 
    })

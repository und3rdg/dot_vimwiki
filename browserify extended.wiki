# GULP + BROWSERIFY + CACHE + BABEL + REACTJS 
    
    
    const is_dev_task = () => {
        // const task_runner = gulp.env._[0]
        const task_runner = process.argv[2]
        let is_dev = false
        is_dev = (task_runner ==="bar") || (task_runner === "watch")
        console.log(
        `--------------------
        is_dev: ${is_dev}
        --------------------`)
        return is_dev
    }
    const IS_DEV = is_dev_task()
    const IS_PROD = !IS_DEV




    const jsEs6 = () => {
        const set_browserify = {
        entries: javascript.bundle.src,
        debug: true,
        // ignoreMissing: true,
        cache: {},
        packageCache: {},
        fullPaths: true,
        }
        // react still is slowest for compiling.
        // ATM about same time as with webpack.
        
        const set_babelify = {
            presets: [
                '@babel/env',
                '@babel/preset-react',
            ],
            "plugins": [
            [
                "@babel/plugin-proposal-class-properties",
            ]
            ],
            sourceMaps: IS_DEV ? true : false,
        }

        let stream = browserify(set_browserify)
        stream = stream.transform(babelify.configure(set_babelify))
        stream.plugin(watchify, {})

        stream = stream.bundle().on('error', err => console.error(err.message))
        stream = stream.pipe(source(javascript.bundle.dist))
        stream = stream.pipe(buffer())

        // enable map if there will by any task running in dev env
        // stream = IS_DEV ? stream.pipe(sourcemaps.init({loadMaps: true})) : stream
        stream = IS_PROD ? stream.pipe(uglify()) : stream
        // stream = IS_DEV ? stream.pipe(sourcemaps.write('./')) : stream
        stream = stream.pipe(duration('javascript es6'))
        stream = stream.pipe(gulp.dest(dest.javascript))

        return stream
    }

    gulp.task('js', ()=>{
        jsEs5()
        jsEs6().on('end', bsync.reload)
    })
    
    
    

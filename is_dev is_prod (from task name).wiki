## helper
    const is_dev_task = () => {
        const task_runner = gulp.env._[0]
        let is_dev = false
        is_dev = (task_runner ==="watch") || (task_runner === "another_task_name")
        return is_dev
    }
    const is_dev = is_dev_task()
    const is_prod = !is_dev

## gulp task

    gulp.task('js', ()=>{
        let stream = gulp.src(...)

        stream = is_prod
            ? stream.pipe(prod_plugin).pipe(...)
            : stream // nothing

        stream = stream.pipe(rest_plugins).pipe(gulp.dest(...))
        
        return stream
    }

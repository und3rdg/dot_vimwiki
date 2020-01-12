var bsync = require("browser-sync").create()


// BROWSER SYNC
gulp.task('browserSync', function() {
  bsync.init({
    proxy: "bl.keepthinking.net/sainsbury",
    host: "bl.keepthinking.net",
    open: false,
    notify: {
      styles: {
        top: 'auto',
        bottom: '0'
      }
    }
  })
})


// css
.pipe(bsync.stream())


// watch

 gulp.task('watchBs', ['browserSync'], function() {
   gulp.watch('src/sass/**/*.scss', ['sass <==>'])
   gulp.watch('src/js/**/*', ['js <==>']).on('change', bsync.reload)
   gulp.watch([ '../php/**/*' ]).on('change', bsync.reload)
 })

 gulp.task('bar', ['watchBs','minify-css', 'js <==>'])

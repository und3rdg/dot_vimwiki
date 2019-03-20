

        export default function(){
            expose_input_type()
            skip_nav()
        }

        function skip_nav(){
            const container = document.querySelector('#skip_nav')
            const links = container.querySelectorAll('a')
            const focusin_handler = () => container.classList.add('focused')
            const focusout_handler = () => container.classList.remove('focused')

            links.forEach(el => el.addEventListener('focusin', focusin_handler, true) )
            links.forEach(el => el.addEventListener('focusout', focusout_handler, true) )
        }

        function expose_input_type() {
            // console.log('🍷🍷🍷')
            const body = document.querySelector('body')
            const tab_keyCode = 9

            const keydown_handler = (e) => e.keyCode === tab_keyCode &&
                body.classList.add('keyboard')
            const click_handler = () => body.classList.remove('keyboard')

            body.addEventListener('keydown', keydown_handler)
            body.addEventListener('mousedown', click_handler)
        }

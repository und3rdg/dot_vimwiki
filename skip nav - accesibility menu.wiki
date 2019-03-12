# CSS
  
    #skip_nav{
        * {
            box-sizing: border-box;
            :before, :after {
                content: none;
                width: auto;
                height: auto;
                background: none;
            }
        }
        overflow: hidden;
        height: 0;
        padding: 0;
        $border_size: 2px;
        margin: -$border_size 10px;
        border: none;
        &.focused {
            height: auto;
        } 
        position: absolute;
        top: 0;
        left: 0;
        z-index: 99999;
        svg.triangle {
            width: 100%;
        }
        ul {
            border: $border_size $color-primary-blue solid;
            padding: 20px;
            background: #fff;
        }
        ul, li{
            list-style: none;
        }
        li {
            a {
                padding: 3px 5px;
                border: 2px transparent solid;
                &:focus {
                    border: 2px $color-primary-blue solid;
                }
            }
        }
    }




## JS

    export default function skip_nav(){
        const container = document.querySelector('#skip_nav')
        const links = container.querySelectorAll('a')
        const focusin_handler = () => container.classList.add('focused')
        const focusout_handler = () => container.classList.remove('focused')
        links.forEach(el => el.addEventListener('focusin', focusin_handler, true) )
        links.forEach(el => el.addEventListener('focusout', focusout_handler, true) )
    }




## HTML

    <div id="skip_nav">
        <ul class="skip_nav">
            <li><a href="#content">Skip to content</a></li>
            <li><a href="" title=""></a></li>
            <li><a href="" title=""></a></li>
        </ul>
        <svg
            class="triangle"
            viewBox="0 0 400 30"
            width="400"
            height="30"
            preserveAspectRatio="none"
            xmlns="http://www.w3.org/2000/svg"
            >
            <polygon points="0,0 200,30 400,0" fill="#569ad4"></polygon>
        </svg>
    </div>

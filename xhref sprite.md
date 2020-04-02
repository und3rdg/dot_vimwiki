# svg sprite svg > use

## SPRITE
    
    <body>
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="position: absolute; width: 0;
        height: 0" id="__SVG_SPRITE_NODE__"><symbol xmlns="http://www.w3.org/2000/svg" viewBox="0 0 165 49"
        id="#v-icon_chevron-down"><g fill-rule="evenodd"><path d="..."></path></g></symbol></svg>
        (...)


## USE

    <a class="promo--content_cta" href="@Model.LinkUrl.Url">View details <span class="icon_arrow">
            <svg width="12px" height="13px"><use xlink:href="#v-icon_chevron-down"></use></svg>
        </span>
    </a>

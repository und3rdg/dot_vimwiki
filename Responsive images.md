
    <picture>
        <source srcset="@Html.Raw(box.Image.GetCropUrl(480, 240))" media="(max-width: 479px)">
        <source srcset="@Html.Raw(@box.Image.GetCropUrl(800, 400))" media="(min-width: 480px) and (max-width: 767px" />
        <source srcset="@Html.Raw(@box.Image.GetCropUrl(450, 275))" media="(min-width: 768px) and (max-width: 999px" />
        <source srcset="@Html.Raw(@box.Image.GetCropUrl(1100, 550))" media="(min-width: 1000px) and (max-width: 1199px" />
        <source srcset="@Html.Raw(@box.Image.GetCropUrl(270, 298))" media="(min-width: 1200px)">
        <img src="@box.Image.GetCropUrl(270, 298)" alt="@box.Image.AltText" />
    </picture>

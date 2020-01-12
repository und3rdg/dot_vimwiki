```
    <img src="<?=kt_get_media_path($feature->media['image'][0], 'media_path_col_span_9')?>"
       srcset="
       <?=kt_get_media_path($feature->media['image'][0], 'media_path_col_span_4')  ?> 300w,
       <?=kt_get_media_path($feature->media['image'][0], 'media_path_col_span_8')  ?> 640w,
       <?=kt_get_media_path($feature->media['image'][0], 'media_path_col_span_12') ?> 940w,
       <?=kt_get_media_path($feature->media['image'][0], 'media_path_lightbox')    ?> 1400w,
       "
       alt="<?=kt_get_media_alt($feature->media['image'][0])?>"
       width="<?=$feature->media['image'][0]->width?>"
       height="<?=$feature->media['image'][0]->height?>"
       />
```

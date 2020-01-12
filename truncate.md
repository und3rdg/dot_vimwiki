## Cut long text at word end, add 3 dots.


    if(!function_exists('truncate'))
    {
        function truncate($text, $chars = 20) {
            if(strlen($text) <= $chars) {
                return $text;
            }
            $text = $text . ' ';
            $text = substr($text, 0, $chars);
            $text = substr($text, 0, strrpos($text, ' '));
            $text = $text . ' ...';
            return $text;
        }
    }

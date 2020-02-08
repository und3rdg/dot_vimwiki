
const url = new URL('https://geo.example.org/api'),
        params = {lat:35.696233, long:139.570431}
    Object.keys(params).forEach(key => url.searchParams.append(key, params[key]))
    
    fetch(url).then(...)
    
    
## Example of implementation
    
    /**
     * Get base url add params to it and construct url with query parameters.
     * @param string with base url 'http://base.url/api'
     * @param object with params {param:'value',p2:'val'}
     * @returns {string} 'http://base.url/api?param=value&p2=val
     */
    export default function createQueryUrl(baseUrl, params) {
        var url = new URL(baseUrl)
        Object.keys(params)
            .forEach(key =>
                url.searchParams.append(key, params[key])
            )
        return url.href
    }

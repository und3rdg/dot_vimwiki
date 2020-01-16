// vim: ft=javascript
// jshint strict: false, undef: false, esversion: 6

//javascript:
(function(){
  host="http://bl.keepthinking.net:4000/";
  site='';
  path=window.location.pathname;
  switch(window.location.hostname){
    case("lloyds.keepthinking.net"):
      site='lloyds';
      break;
    case("www.westkowloon.hk"):
      site='wkcd';
      break;
    case("www-uat.westkowloon.hk"):
      site='wkcd';
      break;
    case("staging.sainsburyarchive.org.uk" || "sainsburyarchive.org.uk"):
      site='sainsbury';
      break;
    default:
      return;
  };
  window.location.href=host+site+path;
})();


javascript:(function(){host="http://bl.keepthinking.net:4000/";site='';path=window.location.pathname;switch(window.location.hostname){case("lloyds.keepthinking.net"):site='lloyds';break;case("www.westkowloon.hk"):site='wkcd';break;case("www-uat.westkowloon.hk"):site='wkcd';break;case("staging.sainsburyarchive.org.uk"||"sainsburyarchive.org.uk"):site='sainsbury';break;default:return;};window.location.href=host+site+path;})();


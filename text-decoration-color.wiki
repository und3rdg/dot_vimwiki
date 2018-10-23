= text-decoration-color =
text-decoration-color is not supported in every browser that mater.
This is neat hack for same effect.

`display: inline` is important

```
    a {
      color: #258;
      text-decoration: underline;
    }
    span {
      color: #d43;
      text-decoration: none;
    }
    <a href="#">
      <span>Text</span>
    </a>
```

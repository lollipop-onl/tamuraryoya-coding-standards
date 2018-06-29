# TSConfig 標準設定

## without Libraries

```
{
  "compilerOptions": {
    "sourceMap": true,
    "target": "es5",
    "moduleResolution": "node",
    "baseUrl": ".",
    "paths": {
      "~/*": [
        "src/scripts/*"
      ]
    }
  }
}
```

## with React

```
{
  "compilerOptions": {
    "sourceMap": true,
    "target": "es5",
    "jsx": "react",
    "moduleResolution": "node",
    "baseUrl": ".",
    "paths": {
      "~/*": [
        "src/scripts/*"
      ]
    }
  }
}
```

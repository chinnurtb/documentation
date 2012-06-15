# compress png

```
ls | grep png$ | xargs -o 7
```

not perfect, because google webmaster tools is stil complaining

# make background transparent

```
convert input.png -transparent white output.png
```

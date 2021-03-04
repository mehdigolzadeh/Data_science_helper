### Zip a file in mac without hidden files:

zip -r data.zip . -x ".*" -x "__MACOSX" -x "*/.DS_Store"

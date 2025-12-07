# melodb
the melody database

Build AWS Lamba layer including music21 python library:
```
sudo bash <<'EOF'
mkdir -p /python && pip install music21 -t /python
MUSIC21_VERSION=$(grep ^Version: /python/music21-*.dist-info/METADATA | awk '{ print $2}')
zip -r aws-lambda-layer-music21-${MUSIC21_VERSION}.zip /python
unzip -l aws-lambda-layer-music21-*.zip
du -h aws-lambda-layer-music21-*.zip
EOF
```
Layer is over 50MB so it will have to be stored in AWS S3.
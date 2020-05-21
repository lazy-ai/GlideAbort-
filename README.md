# GlideAbort-
Glide相关问题
 Glide 4.x 以上 Transformation 导致闪烁增加
```
    private float radius = 0f;

    @Override
    public boolean equals(Object o) {
        if (o instanceof GlideCircleTransform) {
            GlideCircleTransform other = (GlideCircleTransform) o;
            return radius == other.radius;
        }
        return false;
    }

    private static final byte[] ID_BYTES = ID.getBytes(Charset.forName("UTF-8"));

    @Override
    public int hashCode() {
        return Util.hashCode(ID.hashCode(), Util.hashCode(radius));
    }

    @Override
    public void updateDiskCacheKey(@NonNull MessageDigest messageDigest) {
        messageDigest.update(ID_BYTES);

        byte[] radiusData = ByteBuffer.allocate(4).putFloat(radius).array();
        messageDigest.update(radiusData);
    }
```

# 使用阿里云图片上传

```bash
import axios from '@/libs/api.request'

export const oss = () => {
  return axios.request({
    url: '/admin/auth/oss',
    method: 'get'
  })
}

export const getImageMeta = (url) => {
  return axios.request({
    url: url + '?x-oss-process=image/info',
    method: 'get'
  })
}
export const postObject = async ({oss: ossData, key, file, onProgress}) => {
  let data = new FormData()
  data.append('OSSAccessKeyId', ossData.OSSAccessKeyId)
  data.append('success_action_status', 200)
  data.append('policy', ossData.policy)
  data.append('Signature', ossData.Signature)
  data.append('key', key)
  data.append('file', file)
  let url = 'https://pic1.shiyuehehu.com/'
  await axios.request({
    url,
    method: 'post',
    headers: {
      'Content-Type': 'multipart/form-data'
    },
    onUploadProgress: onProgress || null,
    data
  })
  url = url + key
  let meta
  if (file.type.indexOf('image') > -1) {
    meta = await getImageMeta(url)
  } else if (file.type.indexOf('video') > -1) {
    meta = {
      data: {
        ...file.videoMeta,
        size: file.size
      }
    }
  } else {
    throw new Error('当前上传的类型不是image或者video；当前上传的类型是' + file.type)
  }
  console.log('upload-' + file.type + '-meta', meta)
  return {
    url,
    meta: meta.data
  }
}
```

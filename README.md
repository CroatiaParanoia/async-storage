# async-storage

<p align="center">
  <img src="https://img.shields.io/github/workflow/status/CroatiaParanoia/async-storage/CI.svg?sanitize=true" alt="Build Status">
  <!-- <img src="https://img.shields.io/codecov/c/github/CroatiaParanoia/async-storage/master.svg?sanitize=true" alt="Coverage Status"> -->
  <img src="https://img.shields.io/npm/dm/@croatialu/async-storage.svg?sanitize=true" alt="Downloads">
  <img src="https://img.shields.io/npm/v/@croatialu/async-storage.svg?sanitize=true" alt="Version">
  <img src="https://img.shields.io/npm/l/@croatialu/async-storage.svg?sanitize=true" alt="License">
</p>


An asynchronous storage tool


## Useage


### basic
remote, API server, redis, or db, etc...,

``` typescript

import { createAsyncStorage } from '@croatialu/async-storage'

interface RemoteStorageTypes {
  user: { name: string, age: string, gender: 'male' | 'female' }
}

const RemoteStorage = createAsyncStorage({
  async set(key, value){
    return apiServer.post('/api/user-storage', { key, value })
  }
  async get(key){
    return apiServer.get('/api/user-storage')
  }
})

const remoteStorage = new RemoteStorage<RemoteStorageTypes>()

remoteStorage.set('user', { name: 'croatia', age: 23, gender: 'male' })

remoteStorage.set('user', (oldUser) => {
  return { ...oldUser, age: 24 }
})

```


## License

[MIT](./LICENSE) License © 2022 [croatialu](https://github.com/CroatiaParanoia)

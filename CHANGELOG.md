## [1.12.3](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.12.2...v1.12.3) (2024-12-21)


### Bug Fixes

* copy tsconfig to runtime image ([4f29005](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/4f2900570adf79eea7e832588e9ad3ba937939b3))

## [1.12.2](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.12.1...v1.12.2) (2024-12-21)


### Bug Fixes

* copy tsconfig ([bf11716](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/bf117167d38f0c67cdc54674218ae1e9a0bfdf85))

## [1.12.1](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.12.0...v1.12.1) (2024-12-21)


### Bug Fixes

* bun context ([f742fcb](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/f742fcba64e00a2183c429031eff3de37716949b))

# [1.12.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.11.0...v1.12.0) (2024-12-21)


### Features

* setup bun ([a70387a](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/a70387a11d7879e90b94924c2799a687548d3305))

# [1.11.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.10.0...v1.11.0) (2024-12-18)


### Features

* add Dockerfile for bun applications ([128badf](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/128badf9f8ab601452c35e3ee8a3495d3cb41fc5))

# [1.10.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.9.2...v1.10.0) (2024-12-01)


### Features

* run optional install scripts ([5ec9dec](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/5ec9dec5deab11a21c38a097362fa571072bef03))

## [1.9.2](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.9.1...v1.9.2) (2024-12-01)


### Bug Fixes

* fail silently ([836af79](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/836af79ab2d25d27db16cc71f8916d0d3f29bd0f))

## [1.9.1](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.9.0...v1.9.1) (2024-12-01)


### Bug Fixes

* check if tsconfig.build.json file exists before copying ([9e38cfa](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/9e38cfa95ef2b69439b6dac0d68cb81e0ad3aaab))

# [1.9.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.8.1...v1.9.0) (2024-12-01)


### Features

* add nodejs image ([3c7536a](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/3c7536a9f0929afa7f190ff57759df21db351b13))

## [1.8.1](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.8.0...v1.8.1) (2024-08-08)

# [1.8.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.7.2...v1.8.0) (2024-07-09)


### Features

* change web root ([7d300d9](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/7d300d9780846da32cfdfd0e20170fc092983f5a))

## [1.7.2](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.7.1...v1.7.2) (2024-07-09)


### Bug Fixes

* use major version tag of docker publish action ([e73cc85](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/e73cc855f587ca4bacd8cd1918dacb7597ea4ac8))

## [1.7.1](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.7.0...v1.7.1) (2024-07-09)


### Bug Fixes

* variable placeholder in template ([933d8c9](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/933d8c9411fa120dbff269f4b0e766b6bead0f1a))

# [1.7.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.6.1...v1.7.0) (2024-07-09)


### Features

* replace nginx with caddy for nuxt image ([e282912](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/e28291274ed3f75c5547cc23023a827451e91b40))

## [1.6.1](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.6.0...v1.6.1) (2024-07-05)


### Bug Fixes

* revert port change ([1963c63](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/1963c63bfc6d35683fac484e2543e2be3fd755d4))

# [1.6.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.5.0...v1.6.0) (2024-07-04)


### Features

* improve nginx configuration for non-root user ([2cb68e1](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/2cb68e1fb5d0b51fb966aa63599e09cf2b46df3f))

# [1.5.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.4.0...v1.5.0) (2024-06-24)


### Features

* use alpine image for runtime ([2f8d2b3](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/2f8d2b33062c7d7decb4b9b5bd0bdec7c5f6bf16))

# [1.4.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.3.0...v1.4.0) (2024-06-23)


### Features

* remove checkout step, set file permissions for build output ([5ab3d84](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/5ab3d845f9829c41a4c3cc3a59d9a0ce0c102f22))

# [1.3.0](https://github.com/master-software-gmbh/nodejs-deploy-action/compare/v1.2.0...v1.3.0) (2024-06-18)


### Features

* use docker-publish-action ([5c26325](https://github.com/master-software-gmbh/nodejs-deploy-action/commit/5c263253e0d5e172e74affd53ddd30e973c8db7a))

# Changelog

This changelog is auto generated using release-it.


## [0.5.9](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.8...0.5.9) (2025-09-04)

### Chores

* **deps:** update codecov/codecov-action digest to 3e0ce21 ([8d186ae](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/8d186ae496f64c67a0d9e3e878d734467dc32b65))

## [0.5.8](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.7...0.5.8) (2025-09-04)

### Chores

* **deps:** update all dependencies ([dd6dbe2](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/dd6dbe2b8d5a2ca476708d8043ff1917f4ad7f34))

## [0.5.7](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.6...0.5.7) (2025-07-04)

### Chores

* **deps:** update all dependencies ([6f627c9](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/6f627c9e23b941571b00941086cbfe32f658debc))

## [0.5.6](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.5...0.5.6) (2025-05-14)

### Chores

* **deps:** update codecov/codecov-action digest to b203f00 ([a7e06e6](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/a7e06e6c21eef9da60e243815827f7b8e6f4b28c))

## [0.5.5](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.4...0.5.5) (2025-05-05)

### Chores

* **deps:** update all dependencies ([cf4412b](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/cf4412b39a6ca9d09d95801f45c889fda8affb0b))

## [0.5.4](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.3...0.5.4) (2025-04-24)

### Chores

* **deps:** update all dependencies ([0103912](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/0103912488aca6af35a96c101e508ee73d7a8622))

## [0.5.3](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.2...0.5.3) (2025-04-21)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.65 ([97ddd5e](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/97ddd5e76a9f72bd410a068a6e54a1470dd31d4b))

## [0.5.2](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.1...0.5.2) (2025-04-21)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.61 ([d27378a](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/d27378a93987be193ce9b7753bc53f4c2bc38724))

## [0.5.1](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.5.0...0.5.1) (2025-04-20)

### Chores

* **deps:** pin dependencies ([60ddb53](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/60ddb5398311f68b4a8b8f052493774b911b7069))

## [0.5.0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.27...0.5.0) (2025-04-20)

### Features

* add Docker image security scan workflow with Trivy integration and documentation ([65a93d8](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/65a93d822ea0ed5d4291b4aae5589f748a3624fa)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)
* add image scan using tar for reusability to avoid building within the workflow ([a236a23](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/a236a236011b532aa0d8ad7022d9e7f1ec0f55d9)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)
* add image security scan workflow centralized using Trivy ([ec50b4b](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/ec50b4b94d832bee6e60cf5e969e2b9616840f66)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)

### Bug Fixes

* correct Trivy action version syntax in image security scan workflow ([a7af670](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/a7af670705b29ab1c891d04671250341240a6ed6)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)
* rename input variables for clarity in image security scan workflow ([4050a24](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/4050a248a71d675feef6287cd0a018563b198d9e)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)
* update Trivy action version to v0.30.0 for improved security scanning ([da0aa26](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/da0aa266054b652c855be9bf75626a05c22e460f)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)

### Chores

* add .gitignore to exclude .history directory ([3b540cb](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/3b540cbe45d8d82b7927903bcc89a789289cc390)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)

### Documentation

* update actions versions in workflows for consistency and clarity ([f94b50c](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/f94b50c3b8ea70b756e016ba9c570bcfc671bd31)), closes [#35](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/35)

## [0.4.27](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.26...0.4.27) (2025-04-20)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.59 ([17c40c4](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/17c40c47f3cc80fc2c8564c907c2428c8b3cda25))

## [0.4.26](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.25...0.4.26) (2025-04-20)

### Chores

* **deps:** update codecov/codecov-action digest to ad3126e ([ca68475](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/ca68475a2e7b9fae3c11c31762287fb515f4d1cf))

## [0.4.25](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.24...0.4.25) (2025-04-11)

### Chores

* **deps:** update all dependencies ([7cb6dff](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/7cb6dfffcca07a7cb0468e9f9deac4fb1a254d5e))

## [0.4.24](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.23...0.4.24) (2025-03-17)

### Chores

* **deps:** update all dependencies ([167f947](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/167f947d67aa8cf0459efd5af2771f74e250063e))

## [0.4.23](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.22...0.4.23) (2025-02-25)

### Chores

* **deps:** update codecov/codecov-action digest to 2488e99 ([a610fdc](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/a610fdc626956325c569b96ea18c5652acae5bd1))

## [0.4.22](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.21...0.4.22) (2025-02-21)

### Chores

* **deps:** update all dependencies ([04e86e0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/04e86e0e23335ed57f7614bc011f90fe454b1df1))

## [0.4.21](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.20...0.4.21) (2025-02-16)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.51 ([6b012a0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/6b012a0d9483fb4f2b000c956e97639217d6b11c))

## [0.4.20](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.19...0.4.20) (2025-02-14)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.48 ([36da897](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/36da8975de90169f7ca35667a32447c09090b6cf))

## [0.4.19](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.18...0.4.19) (2025-02-11)

### Chores

* **deps:** update codecov/codecov-action digest to 4898080 ([8592052](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/859205268bec435bd9f6c5da612af26bdd1d013f))

## [0.4.18](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.17...0.4.18) (2025-02-10)

### Chores

* **deps:** update all dependencies ([868e37c](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/868e37cdc9242b28312c5069a1aa4eb2d1d1466d))

## [0.4.17](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.16...0.4.17) (2025-01-28)

### Chores

* **deps:** update actions/setup-python digest to 4237552 ([eb7e040](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/eb7e040b03f093b95d2220d65c124691ffa51287))

## [0.4.16](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.15...0.4.16) (2025-01-27)

### Chores

* **deps:** update codecov/codecov-action digest to 2d2cd3c ([bb7e805](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/bb7e8056d22eee7e362a01dd5501e6294970291b))

## [0.4.15](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.14...0.4.15) (2025-01-26)

### Chores

* **deps:** update codecov/codecov-action digest to 13ce06b ([0ac912e](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/0ac912ee7a837585bd0e6669c00e1beb5c61a59a))

## [0.4.14](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.13...0.4.14) (2025-01-24)

### Chores

* **deps:** update codecov/codecov-action digest to 13ce06b ([9dfab78](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/9dfab78a1700c3a6615a9dc07fc27240d1f8a064))

## [0.4.13](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.12...0.4.13) (2025-01-23)

### Chores

* **deps:** update all dependencies ([2d0791e](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/2d0791e21b1a8ab555db8cff0411cd7325cc6ff3))

## [0.4.12](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.11...0.4.12) (2025-01-20)

### Chores

* **deps:** update codecov/codecov-action digest to ad45165 ([39cea75](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/39cea75e9bea5497a4d38ff95c75eb2917d61c9c))

## [0.4.11](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.10...0.4.11) (2025-01-18)

### Chores

* **deps:** update all dependencies ([1b4e1cd](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/1b4e1cdcb30900b466f814cdcbdfe68f54ad494e))

## [0.4.10](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.9...0.4.10) (2025-01-15)

### Chores

* **deps:** update codecov/codecov-action digest to 54a0566 ([cb6bd9d](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/cb6bd9d17b7edfd9eb47ac85cd7198f208d623ec))

## [0.4.9](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.8...0.4.9) (2025-01-14)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.40 ([56f90c7](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/56f90c769f0c3194b091c9510cfb81d50df07056))

## [0.4.8](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.7...0.4.8) (2025-01-08)

### Chores

* **deps:** update all dependencies ([5b315d6](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/5b315d6b5bff139026bb484eacd163f852c86804))

## [0.4.7](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.6...0.4.7) (2024-12-17)

### Chores

* **deps:** update codecov/codecov-action digest to 9b01a34 ([e875673](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/e875673b658c7cec2665c046069d73328c178ef0))

## [0.4.6](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.5...0.4.6) (2024-12-12)

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.35 ([1750bce](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/1750bce79c1104e00664a25c01e8678bccaeb97d))

## [0.4.5](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.4...0.4.5) (2024-12-12)

### Chores

* add license ([9ce9368](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/9ce9368aa0f0bac5ac9ab82ccf3be17d46a7512f))

## [0.4.4](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.3...0.4.4) (2024-12-11)

### Chores

* **deps:** update codecov/codecov-action digest to 5c93f7a ([e0db747](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/e0db747f27021a050de1c9babf1842257b023c71))

## [0.4.3](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.2...0.4.3) (2024-12-08)

### Chores

* **deps:** update dependency juancarlosjr97/renovate-configuration to v0.1.4 ([991a795](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/991a795427e6be089b1991dc134c8692d8d351ff))

## [0.4.2](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.1...0.4.2) (2024-12-08)

### Chores

* **deps:** update dependency juancarlosjr97/renovate-configuration to v0.1.3 ([28f3a97](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/28f3a9713b977c51eac87b89306dea2fba3e4bb3))

## [0.4.1](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.4.0...0.4.1) (2024-12-08)

### Chores

* **deps:** pin dependencies ([a8ada93](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/a8ada93858c50e41bba0fb0a9481e13dfdb0e031))

## [0.4.0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.3.3...0.4.0) (2024-12-08)

### Features

* add comments on release it ([2fe0228](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/2fe022805d0af3fefa185b571a52e56c8e97536c)), closes [#6](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/6)
* add rust workflow for testing ([274a9c6](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/274a9c6ac2e6cf366c377008e94298bb06c493f3)), closes [#5](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/issues/5)

## [0.3.3](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.3.2...0.3.3) (2024-12-07)

### Code Refactoring

* update shared python workflow stage name and job description to codacy ([667daea](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/667daeae0b19b6efdba21ea1268472b11d07ad3c))

## [0.3.2](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.3.1...0.3.2) (2024-12-07)

### Chores

* add pin to renovate shareable config presets ([0726478](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/07264782b51016def0a3579288a515fb1f2839ef))

## [0.3.1](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.3.0...0.3.1) (2024-12-07)

### Chores

* **deps:** pin dependencies ([3792fad](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/3792fadf86bd7a05a04404e6fda6a6f5fb4d339a))

## [0.3.0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.2.0...0.3.0) (2024-12-07)

### Features

* add renovate configuration [skip-ci] ([059499c](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/059499c4097727dca5ae156c11afee3352983114))

### Chores

* **deps:** update juancarlosjr97/release-it-containerized action to v0.7.34 ([50c08d0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/50c08d07d320935ef7734f3e59c74bdcd74f2148))

## [0.2.0](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.1.2...0.2.0) (2024-12-07)

### Features

* add codacy coverage job to the shared workflow for python tests ([df31fad](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/df31fadbf41fdcbd418d4ddfd0b0758715af87e8))

## [0.1.2](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.1.1...0.1.2) (2024-12-07)

### Documentation

* update README with right title ([408fb0f](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/408fb0f83995731ae706dbfce3d93c50984d2f44))

## [0.1.1](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/compare/0.1.0...0.1.1) (2024-12-07)

### Documentation

* add details about the release-automation workflow ([ce4e4e5](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/ce4e4e5d4782961edf4cf29ef54bbd7b69433883))

## 0.1.0 (2024-12-07)

### Features

* add release automation to the project ([15555df](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/15555df3387bdf1faff6d03cf485858fa3c14e5d))
* add shared github workflow for python test ([97cebdc](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/97cebdc401ca70750135aac39baf013d0988a506))
* add shared github workflow for release automation ([076ddf4](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/076ddf4fac551ed31b00d7afc2041dfa18468ad8))

### Documentation

* add initial README and project ([c7df490](https://github.com/juancarlosjr97/github-actions-workflows-to-rule-them-all/commit/c7df490bc762b0dab94771702551d03086d06b9a))

# vrchat

[![vrchat - npm](https://img.shields.io/npm/v/vrchat.svg)](https://www.npmjs.com/package/vrchat)
[![Build And Lint](https://github.com/calmery/vrchat/actions/workflows/build-and-lint.yml/badge.svg?branch=develop)](https://github.com/calmery/vrchat/actions/workflows/build-and-lint.yml)
[![Commitizen Friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

Unofficial VRChat API Client 🤫

## Installation

```
$ npm i vrchat
```

## Usage

```ts
import { VRChat, VRChatTFAMethod } from "vrchat";

const main = async () => {
  const vrchat = new VRChat();

  const tfa = await vrchat.login(
    process.env.VRCHAT_USERNAME,
    process.env.VRCHAT_PASSWORD
  );

  if (tfa && tfa.includes(VRChatTFAMethod.TimeBasedOneTimePassword)) {
    await vrchat.verifyTfa(
      VRChatTFAMethod.TimeBasedOneTimePassword,
      process.env.VRCHAT_TFA_CODE
    );
  }

  console.log(vrchat.auth);
  console.log(vrchat.twoFactorAuth);

  // await vrchat.get("...");
};

main();
```

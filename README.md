# The Lost Grimoire

_At Zaros Oasis an old book was found buried deep beneath the dunes, it had ten thousand pages describing wizards and their runes_

## Introduction

This is a storage contract for the traits and affinities of _Forgotten Runes Wizard Cult_ wizards.

The contract exposes the `storeWizardTraits()` method that can be called by anyone to submit the traits and the name of a wizard. These are verified through a Merkle Tree generated beforehand.
The Merkle Tree is constructed with the data files in `./data` which are generated by the decoder in `./scripts/decoder` using the on-chain data stored by the FRWC team [see decoding script by dotta](https://gist.github.com/cryppadotta/375dee1903598f5163e2c1d7d3ce9db9)

Find encoding and merkle tree generation in `./scripts/helpers/merkletree`.

A frontend tool to generate the Merkle Proofs and cosntruct the Verification transaction can be found [here](https://wizards-verification-app.vercel.app/)

## Public Read Endpoints

The contract has public endpoints to query traits and affinities for wizards:

`getWizardTraits(uint256 wizardId)` returns all traits in order: _background, body, familiar, head, rune, prop_

`getWizardName(uint256 wizardId)` returns the name of the wizard

`getTraitIdentityAffinities(uint16 traitId)` returns all identity affinities for a given trait

`getTraitPositiveAffinities(uint16 traitId)` returns all positive affinities for a given trait

`getTraitAffinities(uint16 traitId)` returns all affinities for a given trait (de-duplicated)

`getAffinityOccurrences(uint16 affinityId)`returns the occurrence of an affinity across the entire collection (rarity)

`getWizardAffinities(uint256 wizardId)` returns the list of affinities of a wizard based on

`getWizardIdentityAffinities(uint256 wizardId)` returns the list of identity affinities of a wizard based

`getWizardPositiveAffinities(uint256 wizardId)` returns the list of positive affinities of a wizard based

`getWizardAffinityCount(uint256 wizardId, uint16 affinity)` returns how many times a wizard has an affinity

`getWizardIdentityAffinityCount(uint256 wizardId, uint16 affinity)` returns how many times a wizard has an identity affinity

`getWizardPositiveAffinityCount(uint256 wizardId, uint16 affinity)` returns how many times a wizard has an positive affinity

`wizardHasTrait(uint256 wizardId, uint16 trait)` returns if the wizard has a trait or not

`hasTraitsStored(uint256 wizardId)` returns if the wizard has traits stored

## Commands

Set environment variables in a new `.env` file

Install dependencies  
`npm install`

Run Decoder to generate source files
`yarn decode`

Run tests  
`yarn test`

Run local deployment  
`yarn deploy`

Run rinkeby deployment (see comments in `./scripts/run_deploy.ts`)  
`yarn deploy --network rinkeby`

Run mainnet deployment (see comments in `./scripts/run_deploy.ts`)  
`yarn deploy --network mainnet`
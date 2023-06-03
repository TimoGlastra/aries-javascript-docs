import DocCardList from '@theme/DocCardList';

# Modules

Modules in Aries Framework JavaScript are a way to extend the functionality of the framework. They are a collection of features that can be used in your application. They can be used to add support for new protocols, new storage mechanisms, new credential formats, or different ledgers.

### AnonCreds

[AnonCreds](https://hyperledger.github.io/anoncreds-spec/) is a credential format that contains a number of privacy-preserving preserving features. The AnonCreds integration is powered by the AnonCreds (`@aries-framework/anoncreds`) package.

<DocCardList items={[
{ type: 'link', label: 'AnonCreds', href: './anoncreds', docId: 'modules/anoncreds' }
]} />

#### AnonCreds Implementation

For using AnonCreds in your application

<DocCardList items={[
{ type: 'link', label: 'AnonCreds RS', href: './anoncreds-rs', docId: 'modules/anoncreds-rs' },
{ type: 'link', label: 'Indy SDK (deprecated)', href: './indy-sdk', docId: 'modules/indy-sdk' },
]} />

#### AnonCreds Registries

<DocCardList items={[
{ type: 'link', label: 'cheqd', href: './cheqd', docId: 'modules/cheqd' },
{ type: 'link', label: 'Indy VDR', href: './indy-vdr', docId: 'modules/indy-vdr' },
{ type: 'link', label: 'Indy SDK (deprecated)', href: './indy-sdk', docId: 'modules/indy-sdk' },
]} />

### DID Methods

<DocCardList items={[
{ type: 'link', label: 'cheqd', href: './cheqd', docId: 'modules/cheqd' }
]} />

### Wallet

### Storage

### W3C Verifiable Credentials

### Miscellaneous

- Tenants

# VueFesJapan

## 概要
* 日時: 2018/11/03
* 場所: UDX


## Unit testing a Vuex store  
* Speeker: Edd Yerburgh

## talk
### Unit Test
* Verify code works
* Document code
* Enable workflows

### Vuex
* Components
* Actions
* State

### Vuex store
* Actions
* Mutations
* State
* Getters

### Unit Test Approch
1. Don't
  * Unit Tests take time to write
  * e2e test test store implicitly
2. Test store parts seperatery
  * Mutationd
  * State
    - Call with state object and payload
    - assert state value update
  * Geters
    - Call with state object (resolved getters)
    - Assert return value
  * Action
    - Call with mocked store context (payload)
    - Assert that action commits data
    - Testing store parts seperately
      - Fine grained
      - Brittle
3. Test a
  * fetch items -> store -> getters.displayItems
  * Steps
    - Install Vuex
      - vue->localVue->new.Vue()
      - on localVue Constructor `localVue.use(Vuex)`
    - Create a store instance
      - `const store = new Vuex.Store({})`
    - Test instance
      - `await store.dipatch('fetchItems')`
      - `const store = new Vuex.Store(storeConfig)`
      - Less Specific
      - Not brittle

### Integration Test?
* npm run test:unit
* npm run test:integration


*

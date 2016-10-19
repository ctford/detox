;; ROAD MAP

### TODO
 X add build to travis
 X improve error and success result return types - errors should be presented as map of key to error details
   - {:valid true :result {}}  {:valid false :result {:k []}}
 X implement translation
 X consolidate ```at``` and ```at*```
 X target both clj and cljs - run tests in both environments
 X convert tests to clojure.test
    X use plugin to replace midje autotest
 - verify that arguments to higher-order validators are validators
 - write README
 - if using a nested-selector with multi-selectors, verify that each selector only returns a single value
 X roll detox.model back into detox.core
 - write test that demos that parsing can be done with multi-nested validator
 - if validator multiple values, perhaps someway of indexing them in error path?
 - get some codox involved
 - make detox.schema ns
 - make assertion that selectors are of correct type
 - write some tests for the macros

### QUESTIONS
 - For errors, should unparsed or transformed values be preserved in error value?
 - Should mandatory be default, with optional values having a special wrapper?
 - can there be more than one error with the same key?
 - should identifier (e.g. [:address :line-1]) be separated from base failure (e.g. [:greater-than])?
 - do I need to add in dependencies?
 - What happens if translate is called on success result?
 X What happens for lens law violation? I.e. I run an update, then a get (i.e. the modification changes the results of the selector)
 - should from-map provide strictness of keys that schema can?
 - Is the test of presence a special thing, that can't just be applied as a validator??

### ISSUES
 - if the structure of the thing to be validated is wrong, then the nested validators can blow up
 - macros currently remove the possibility for doc strings
 - FIXME IMPORTANT what to do if validators on multiple values are dependent on optional values?

 - FIXME difficulty with group validations, let's say the first validator has some updates that succeed,
 - but others that fail (so error is returned), should the subsequent validators be able to see those updates?
 - FIXME group probably doesn't deal with the short-circuit return, potentially neither does at

### IDEAS
 - Could add a key to error map called scope, which includes the larger scope of data that failed

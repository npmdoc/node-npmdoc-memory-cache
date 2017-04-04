# api documentation for  [memory-cache (v0.1.6)](https://github.com/ptarjan/node-cache#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-memory-cache.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-memory-cache) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-memory-cache.svg)](https://travis-ci.org/npmdoc/node-npmdoc-memory-cache)
#### A simple in-memory cache. put(), get() and del()

[![NPM](https://nodei.co/npm/memory-cache.png?downloads=true)](https://www.npmjs.com/package/memory-cache)

[![apidoc](https://npmdoc.github.io/node-npmdoc-memory-cache/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-memory-cache_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-memory-cache/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-memory-cache/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-memory-cache/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Paul Tarjan",
        "email": "npm@paulisageek.com"
    },
    "bugs": {
        "url": "https://github.com/ptarjan/node-cache/issues"
    },
    "contributors": [
        {
            "name": "Ramon Snir",
            "email": "ramon@dynamicyield.com"
        },
        {
            "name": "Jacob Wenger",
            "email": "wenger.jacob@gmail.com"
        }
    ],
    "dependencies": {},
    "description": "A simple in-memory cache. put(), get() and del()",
    "devDependencies": {
        "chai": "^2.2.0",
        "gulp": "^3.8.11",
        "gulp-exit": "0.0.2",
        "gulp-istanbul": "^0.7.0",
        "gulp-jshint": "^1.10.0",
        "gulp-mocha": "^2.0.1",
        "jshint-stylish": "^1.0.1",
        "sinon": "^1.14.1",
        "sinon-chai": "^2.7.0"
    },
    "directories": {},
    "dist": {
        "shasum": "2ed9933ed7a8c718249be7366f7ca8749acf8a24",
        "tarball": "https://registry.npmjs.org/memory-cache/-/memory-cache-0.1.6.tgz"
    },
    "gitHead": "cb26698fd2561c2ffadfc210c0a3dae08862bc8a",
    "homepage": "https://github.com/ptarjan/node-cache#readme",
    "keywords": [
        "cache",
        "ram",
        "simple",
        "storage"
    ],
    "license": "BSD-2-Clause",
    "main": "./index.js",
    "maintainers": [
        {
            "name": "ptarjan",
            "email": "npm@paulisageek.com"
        }
    ],
    "name": "memory-cache",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/ptarjan/node-cache.git"
    },
    "scripts": {
        "test": "gulp test"
    },
    "version": "0.1.6"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module memory-cache](#apidoc.module.memory-cache)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>clear ()](#apidoc.element.memory-cache.clear)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>debug (bool)](#apidoc.element.memory-cache.debug)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>del (key)](#apidoc.element.memory-cache.del)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>get (key)](#apidoc.element.memory-cache.get)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>hits ()](#apidoc.element.memory-cache.hits)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>keys ()](#apidoc.element.memory-cache.keys)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>memsize ()](#apidoc.element.memory-cache.memsize)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>misses ()](#apidoc.element.memory-cache.misses)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>put (key, value, time, timeoutCallback)](#apidoc.element.memory-cache.put)
1.  [function <span class="apidocSignatureSpan">memory-cache.</span>size ()](#apidoc.element.memory-cache.size)



# <a name="apidoc.module.memory-cache"></a>[module memory-cache](#apidoc.module.memory-cache)

#### <a name="apidoc.element.memory-cache.clear"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>clear ()](#apidoc.element.memory-cache.clear)
- description and source-code
```javascript
clear = function () {
  for (var key in cache) {
    clearTimeout(cache[key].timeout);
  }
  size = 0;
  cache = Object.create(null);
  if (debug) {
    hitCount = 0;
    missCount = 0;
  }
}
```
- example usage
```shell
...
chai.use(sinonChai);


describe('node-cache', function() {
beforeEach(function() {
  clock = sinon.useFakeTimers();

  cache.clear();
});

afterEach(function() {
  clock.restore();
});

describe('put()', function() {
...
```

#### <a name="apidoc.element.memory-cache.debug"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>debug (bool)](#apidoc.element.memory-cache.debug)
- description and source-code
```javascript
debug = function (bool) {
  debug = bool;
}
```
- example usage
```shell
...

  afterEach(function() {
clock.restore();
  });

  describe('put()', function() {
before(function() {
  cache.debug(false);
});

it('should allow adding a new item to the cache', function() {
  expect(function() {
    cache.put('key', 'value');
  }).to.not.throw();
});
...
```

#### <a name="apidoc.element.memory-cache.del"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>del (key)](#apidoc.element.memory-cache.del)
- description and source-code
```javascript
del = function (key) {
  var canDelete = true;

  var oldRecord = cache[key];
  if (oldRecord) {
    clearTimeout(oldRecord.timeout);
    if (!isNaN(oldRecord.expire) && oldRecord.expire < Date.now()) {
      canDelete = false;
    }
  } else {
    canDelete = false;
  }

  if (canDelete) {
    _del(key);
  }

  return canDelete;
}
```
- example usage
```shell
...

  describe('del()', function() {
before(function() {
  cache.debug(false);
});

it('should return false given a key for an empty cache', function() {
  expect(cache.del('miss')).to.be.false;
});

it('should return false given a key not in a non-empty cache', function() {
  cache.put('key', 'value');
  expect(cache.del('miss')).to.be.false;
});
...
```

#### <a name="apidoc.element.memory-cache.get"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>get (key)](#apidoc.element.memory-cache.get)
- description and source-code
```javascript
get = function (key) {
  var data = cache[key];
  if (typeof data != "undefined") {
    if (isNaN(data.expire) || data.expire >= Date.now()) {
      if (debug) hitCount++;
      return data.value;
    } else {
      // free some space
      if (debug) missCount++;
      size--;
      delete cache[key];
    }
  } else if (debug) {
    missCount++;
  }
  return null;
}
```
- example usage
```shell
...

'''javascript
var cache = require('memory-cache');

// now just use the cache

cache.put('foo', 'bar');
console.log(cache.get('foo'));

// that wasn't too interesting, here's the good part

cache.put('houdini', 'disappear', 100, function(key, value) {
    console.log(key + ' did ' + value);
}); // Time in ms
...
```

#### <a name="apidoc.element.memory-cache.hits"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>hits ()](#apidoc.element.memory-cache.hits)
- description and source-code
```javascript
hits = function () {
  return hitCount;
}
```
- example usage
```shell
...
  expect(cache.size()).to.equal(0);
});

it('should reset the debug cache hits', function() {
  cache.debug(true);
  cache.put('key', 'value');
  cache.get('key');
  expect(cache.hits()).to.equal(1);
  cache.clear();
  expect(cache.hits()).to.equal(0);
});

it('should reset the debug cache misses', function() {
  cache.debug(true);
  cache.put('key', 'value');
...
```

#### <a name="apidoc.element.memory-cache.keys"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>keys ()](#apidoc.element.memory-cache.keys)
- description and source-code
```javascript
keys = function () {
  return Object.keys(cache);
}
```
- example usage
```shell
...
};

exports.misses = function() {
  return missCount;
};

exports.keys = function() {
  return Object.keys(cache);
};
...
```

#### <a name="apidoc.element.memory-cache.memsize"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>memsize ()](#apidoc.element.memory-cache.memsize)
- description and source-code
```javascript
memsize = function () {
  var size = 0,
    key;
  for (key in cache) {
    size++;
  }
  return size;
}
```
- example usage
```shell
...

  describe('memsize()', function() {
before(function() {
  cache.debug(false);
});

it('should return 0 given a fresh cache', function() {
  expect(cache.memsize()).to.equal(0);
});

it('should return 1 after adding a single item to the cache', function() {
  cache.put('key', 'value');
  expect(cache.memsize()).to.equal(1);
});
...
```

#### <a name="apidoc.element.memory-cache.misses"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>misses ()](#apidoc.element.memory-cache.misses)
- description and source-code
```javascript
misses = function () {
  return missCount;
}
```
- example usage
```shell
...
  expect(cache.hits()).to.equal(0);
});

it('should reset the debug cache misses', function() {
  cache.debug(true);
  cache.put('key', 'value');
  cache.get('miss1');
  expect(cache.misses()).to.equal(1);
  cache.clear();
  expect(cache.misses()).to.equal(0);
});

it('should cancel the timeout callbacks for all existing keys', function() {
  var spy1 = sinon.spy();
  var spy2 = sinon.spy();
...
```

#### <a name="apidoc.element.memory-cache.put"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>put (key, value, time, timeoutCallback)](#apidoc.element.memory-cache.put)
- description and source-code
```javascript
put = function (key, value, time, timeoutCallback) {
  if (debug) {
    console.log('caching: %s = %j (@%s)', key, value, time);
  }

  if (typeof time !== 'undefined' && (typeof time !== 'number' || isNaN(time) || time <= 0)) {
    throw new Error('Cache timeout must be a positive number');
  } else if (typeof timeoutCallback !== 'undefined' && typeof timeoutCallback !== 'function') {
    throw new Error('Cache timeout callback must be a function');
  }

  var oldRecord = cache[key];
  if (oldRecord) {
    clearTimeout(oldRecord.timeout);
  } else {
    size++;
  }

  var record = {
    value: value,
    expire: time + Date.now()
  };

  if (!isNaN(record.expire)) {
    record.timeout = setTimeout(function() {
      _del(key);
      if (timeoutCallback) {
        timeoutCallback(key, value);
      }
    }, time);
  }

  cache[key] = record;

  return value;
}
```
- example usage
```shell
...
## Usage

'''javascript
var cache = require('memory-cache');

// now just use the cache

cache.put('foo', 'bar');
console.log(cache.get('foo'));

// that wasn't too interesting, here's the good part

cache.put('houdini', 'disappear', 100, function(key, value) {
    console.log(key + ' did ' + value);
}); // Time in ms
...
```

#### <a name="apidoc.element.memory-cache.size"></a>[function <span class="apidocSignatureSpan">memory-cache.</span>size ()](#apidoc.element.memory-cache.size)
- description and source-code
```javascript
size = function () {
  return size;
}
```
- example usage
```shell
...
  expect(cache.get('key')).to.equal('value');
  expect(cache.del('key')).to.be.true;
  expect(cache.get('key')).to.be.null;
});

it('should decrement the cache size by 1', function() {
  cache.put('key', 'value');
  expect(cache.size()).to.equal(1);
  expect(cache.del('key')).to.be.true;
  expect(cache.size()).to.equal(0);
});

it('should not remove other keys in the cache', function() {
  cache.put('key1', 'value1');
  cache.put('key2', 'value2');
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

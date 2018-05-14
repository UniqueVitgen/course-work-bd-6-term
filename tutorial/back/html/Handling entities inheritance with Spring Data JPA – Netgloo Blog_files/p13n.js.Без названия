/******/ (function(modules) { // webpackBootstrap
/******/ 	// The module cache
/******/ 	var installedModules = {};
/******/
/******/ 	// The require function
/******/ 	function __webpack_require__(moduleId) {
/******/
/******/ 		// Check if module is in cache
/******/ 		if(installedModules[moduleId]) {
/******/ 			return installedModules[moduleId].exports;
/******/ 		}
/******/ 		// Create a new module (and put it into the cache)
/******/ 		var module = installedModules[moduleId] = {
/******/ 			i: moduleId,
/******/ 			l: false,
/******/ 			exports: {}
/******/ 		};
/******/
/******/ 		// Execute the module function
/******/ 		modules[moduleId].call(module.exports, module, module.exports, __webpack_require__);
/******/
/******/ 		// Flag the module as loaded
/******/ 		module.l = true;
/******/
/******/ 		// Return the exports of the module
/******/ 		return module.exports;
/******/ 	}
/******/
/******/
/******/ 	// expose the modules object (__webpack_modules__)
/******/ 	__webpack_require__.m = modules;
/******/
/******/ 	// expose the module cache
/******/ 	__webpack_require__.c = installedModules;
/******/
/******/ 	// define getter function for harmony exports
/******/ 	__webpack_require__.d = function(exports, name, getter) {
/******/ 		if(!__webpack_require__.o(exports, name)) {
/******/ 			Object.defineProperty(exports, name, {
/******/ 				configurable: false,
/******/ 				enumerable: true,
/******/ 				get: getter
/******/ 			});
/******/ 		}
/******/ 	};
/******/
/******/ 	// getDefaultExport function for compatibility with non-harmony modules
/******/ 	__webpack_require__.n = function(module) {
/******/ 		var getter = module && module.__esModule ?
/******/ 			function getDefault() { return module['default']; } :
/******/ 			function getModuleExports() { return module; };
/******/ 		__webpack_require__.d(getter, 'a', getter);
/******/ 		return getter;
/******/ 	};
/******/
/******/ 	// Object.prototype.hasOwnProperty.call
/******/ 	__webpack_require__.o = function(object, property) { return Object.prototype.hasOwnProperty.call(object, property); };
/******/
/******/ 	// __webpack_public_path__
/******/ 	__webpack_require__.p = "";
/******/
/******/ 	// Load entry module and return exports
/******/ 	return __webpack_require__(__webpack_require__.s = 73);
/******/ })
/************************************************************************/
/******/ ([
/* 0 */
/***/ (function(module, exports) {

var core = module.exports = { version: '2.5.1' };
if (typeof __e == 'number') __e = core; // eslint-disable-line no-undef


/***/ }),
/* 1 */
/***/ (function(module, exports, __webpack_require__) {

var global = __webpack_require__(3);
var core = __webpack_require__(0);
var ctx = __webpack_require__(6);
var hide = __webpack_require__(9);
var PROTOTYPE = 'prototype';

var $export = function (type, name, source) {
  var IS_FORCED = type & $export.F;
  var IS_GLOBAL = type & $export.G;
  var IS_STATIC = type & $export.S;
  var IS_PROTO = type & $export.P;
  var IS_BIND = type & $export.B;
  var IS_WRAP = type & $export.W;
  var exports = IS_GLOBAL ? core : core[name] || (core[name] = {});
  var expProto = exports[PROTOTYPE];
  var target = IS_GLOBAL ? global : IS_STATIC ? global[name] : (global[name] || {})[PROTOTYPE];
  var key, own, out;
  if (IS_GLOBAL) source = name;
  for (key in source) {
    // contains in native
    own = !IS_FORCED && target && target[key] !== undefined;
    if (own && key in exports) continue;
    // export native or passed
    out = own ? target[key] : source[key];
    // prevent global pollution for namespaces
    exports[key] = IS_GLOBAL && typeof target[key] != 'function' ? source[key]
    // bind timers to global for call from export context
    : IS_BIND && own ? ctx(out, global)
    // wrap global constructors for prevent change them in library
    : IS_WRAP && target[key] == out ? (function (C) {
      var F = function (a, b, c) {
        if (this instanceof C) {
          switch (arguments.length) {
            case 0: return new C();
            case 1: return new C(a);
            case 2: return new C(a, b);
          } return new C(a, b, c);
        } return C.apply(this, arguments);
      };
      F[PROTOTYPE] = C[PROTOTYPE];
      return F;
    // make static versions for prototype methods
    })(out) : IS_PROTO && typeof out == 'function' ? ctx(Function.call, out) : out;
    // export proto methods to core.%CONSTRUCTOR%.methods.%NAME%
    if (IS_PROTO) {
      (exports.virtual || (exports.virtual = {}))[key] = out;
      // export proto methods to core.%CONSTRUCTOR%.prototype.%NAME%
      if (type & $export.R && expProto && !expProto[key]) hide(expProto, key, out);
    }
  }
};
// type bitmap
$export.F = 1;   // forced
$export.G = 2;   // global
$export.S = 4;   // static
$export.P = 8;   // proto
$export.B = 16;  // bind
$export.W = 32;  // wrap
$export.U = 64;  // safe
$export.R = 128; // real proto method for `library`
module.exports = $export;


/***/ }),
/* 2 */
/***/ (function(module, exports, __webpack_require__) {

var store = __webpack_require__(47)('wks');
var uid = __webpack_require__(36);
var Symbol = __webpack_require__(3).Symbol;
var USE_SYMBOL = typeof Symbol == 'function';

var $exports = module.exports = function (name) {
  return store[name] || (store[name] =
    USE_SYMBOL && Symbol[name] || (USE_SYMBOL ? Symbol : uid)('Symbol.' + name));
};

$exports.store = store;


/***/ }),
/* 3 */
/***/ (function(module, exports) {

// https://github.com/zloirock/core-js/issues/86#issuecomment-115759028
var global = module.exports = typeof window != 'undefined' && window.Math == Math
  ? window : typeof self != 'undefined' && self.Math == Math ? self
  // eslint-disable-next-line no-new-func
  : Function('return this')();
if (typeof __g == 'number') __g = global; // eslint-disable-line no-undef


/***/ }),
/* 4 */
/***/ (function(module, exports) {

module.exports = function (it) {
  return typeof it === 'object' ? it !== null : typeof it === 'function';
};


/***/ }),
/* 5 */
/***/ (function(module, exports, __webpack_require__) {

var anObject = __webpack_require__(7);
var IE8_DOM_DEFINE = __webpack_require__(81);
var toPrimitive = __webpack_require__(82);
var dP = Object.defineProperty;

exports.f = __webpack_require__(8) ? Object.defineProperty : function defineProperty(O, P, Attributes) {
  anObject(O);
  P = toPrimitive(P, true);
  anObject(Attributes);
  if (IE8_DOM_DEFINE) try {
    return dP(O, P, Attributes);
  } catch (e) { /* empty */ }
  if ('get' in Attributes || 'set' in Attributes) throw TypeError('Accessors not supported!');
  if ('value' in Attributes) O[P] = Attributes.value;
  return O;
};


/***/ }),
/* 6 */
/***/ (function(module, exports, __webpack_require__) {

// optional / simple context binding
var aFunction = __webpack_require__(16);
module.exports = function (fn, that, length) {
  aFunction(fn);
  if (that === undefined) return fn;
  switch (length) {
    case 1: return function (a) {
      return fn.call(that, a);
    };
    case 2: return function (a, b) {
      return fn.call(that, a, b);
    };
    case 3: return function (a, b, c) {
      return fn.call(that, a, b, c);
    };
  }
  return function (/* ...args */) {
    return fn.apply(that, arguments);
  };
};


/***/ }),
/* 7 */
/***/ (function(module, exports, __webpack_require__) {

var isObject = __webpack_require__(4);
module.exports = function (it) {
  if (!isObject(it)) throw TypeError(it + ' is not an object!');
  return it;
};


/***/ }),
/* 8 */
/***/ (function(module, exports, __webpack_require__) {

// Thank's IE8 for his funny defineProperty
module.exports = !__webpack_require__(10)(function () {
  return Object.defineProperty({}, 'a', { get: function () { return 7; } }).a != 7;
});


/***/ }),
/* 9 */
/***/ (function(module, exports, __webpack_require__) {

var dP = __webpack_require__(5);
var createDesc = __webpack_require__(38);
module.exports = __webpack_require__(8) ? function (object, key, value) {
  return dP.f(object, key, createDesc(1, value));
} : function (object, key, value) {
  object[key] = value;
  return object;
};


/***/ }),
/* 10 */
/***/ (function(module, exports) {

module.exports = function (exec) {
  try {
    return !!exec();
  } catch (e) {
    return true;
  }
};


/***/ }),
/* 11 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var $at = __webpack_require__(93)(true);

// 21.1.3.27 String.prototype[@@iterator]()
__webpack_require__(40)(String, 'String', function (iterated) {
  this._t = String(iterated); // target
  this._i = 0;                // next index
// 21.1.5.2.1 %StringIteratorPrototype%.next()
}, function () {
  var O = this._t;
  var index = this._i;
  var point;
  if (index >= O.length) return { value: undefined, done: true };
  point = $at(O, index);
  this._i += point.length;
  return { value: point, done: false };
});


/***/ }),
/* 12 */
/***/ (function(module, exports) {

module.exports = {};


/***/ }),
/* 13 */
/***/ (function(module, exports, __webpack_require__) {

// 7.1.13 ToObject(argument)
var defined = __webpack_require__(32);
module.exports = function (it) {
  return Object(defined(it));
};


/***/ }),
/* 14 */
/***/ (function(module, exports) {

var hasOwnProperty = {}.hasOwnProperty;
module.exports = function (it, key) {
  return hasOwnProperty.call(it, key);
};


/***/ }),
/* 15 */
/***/ (function(module, exports) {

var toString = {}.toString;

module.exports = function (it) {
  return toString.call(it).slice(8, -1);
};


/***/ }),
/* 16 */
/***/ (function(module, exports) {

module.exports = function (it) {
  if (typeof it != 'function') throw TypeError(it + ' is not a function!');
  return it;
};


/***/ }),
/* 17 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(92), __esModule: true };

/***/ }),
/* 18 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(98);
var global = __webpack_require__(3);
var hide = __webpack_require__(9);
var Iterators = __webpack_require__(12);
var TO_STRING_TAG = __webpack_require__(2)('toStringTag');

var DOMIterables = ('CSSRuleList,CSSStyleDeclaration,CSSValueList,ClientRectList,DOMRectList,DOMStringList,' +
  'DOMTokenList,DataTransferItemList,FileList,HTMLAllCollection,HTMLCollection,HTMLFormElement,HTMLSelectElement,' +
  'MediaList,MimeTypeArray,NamedNodeMap,NodeList,PaintRequestList,Plugin,PluginArray,SVGLengthList,SVGNumberList,' +
  'SVGPathSegList,SVGPointList,SVGStringList,SVGTransformList,SourceBufferList,StyleSheetList,TextTrackCueList,' +
  'TextTrackList,TouchList').split(',');

for (var i = 0; i < DOMIterables.length; i++) {
  var NAME = DOMIterables[i];
  var Collection = global[NAME];
  var proto = Collection && Collection.prototype;
  if (proto && !proto[TO_STRING_TAG]) hide(proto, TO_STRING_TAG, NAME);
  Iterators[NAME] = Iterators.Array;
}


/***/ }),
/* 19 */
/***/ (function(module, exports, __webpack_require__) {

var ctx = __webpack_require__(6);
var call = __webpack_require__(56);
var isArrayIter = __webpack_require__(57);
var anObject = __webpack_require__(7);
var toLength = __webpack_require__(24);
var getIterFn = __webpack_require__(43);
var BREAK = {};
var RETURN = {};
var exports = module.exports = function (iterable, entries, fn, that, ITERATOR) {
  var iterFn = ITERATOR ? function () { return iterable; } : getIterFn(iterable);
  var f = ctx(fn, that, entries ? 2 : 1);
  var index = 0;
  var length, step, iterator, result;
  if (typeof iterFn != 'function') throw TypeError(iterable + ' is not iterable!');
  // fast case for arrays with default iterator
  if (isArrayIter(iterFn)) for (length = toLength(iterable.length); length > index; index++) {
    result = entries ? f(anObject(step = iterable[index])[0], step[1]) : f(iterable[index]);
    if (result === BREAK || result === RETURN) return result;
  } else for (iterator = iterFn.call(iterable); !(step = iterator.next()).done;) {
    result = call(iterator, f, step.value, entries);
    if (result === BREAK || result === RETURN) return result;
  }
};
exports.BREAK = BREAK;
exports.RETURN = RETURN;


/***/ }),
/* 20 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


exports.__esModule = true;

var _isIterable2 = __webpack_require__(109);

var _isIterable3 = _interopRequireDefault(_isIterable2);

var _getIterator2 = __webpack_require__(27);

var _getIterator3 = _interopRequireDefault(_getIterator2);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

exports["default"] = function () {
  function sliceIterator(arr, i) {
    var _arr = [];
    var _n = true;
    var _d = false;
    var _e = undefined;

    try {
      for (var _i = (0, _getIterator3["default"])(arr), _s; !(_n = (_s = _i.next()).done); _n = true) {
        _arr.push(_s.value);

        if (i && _arr.length === i) break;
      }
    } catch (err) {
      _d = true;
      _e = err;
    } finally {
      try {
        if (!_n && _i["return"]) _i["return"]();
      } finally {
        if (_d) throw _e;
      }
    }

    return _arr;
  }

  return function (arr, i) {
    if (Array.isArray(arr)) {
      return arr;
    } else if ((0, _isIterable3["default"])(Object(arr))) {
      return sliceIterator(arr, i);
    } else {
      throw new TypeError("Invalid attempt to destructure non-iterable instance");
    }
  };
}();

/***/ }),
/* 21 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(75), __esModule: true };

/***/ }),
/* 22 */
/***/ (function(module, exports, __webpack_require__) {

// 19.1.2.14 / 15.2.3.14 Object.keys(O)
var $keys = __webpack_require__(77);
var enumBugKeys = __webpack_require__(48);

module.exports = Object.keys || function keys(O) {
  return $keys(O, enumBugKeys);
};


/***/ }),
/* 23 */
/***/ (function(module, exports, __webpack_require__) {

// to indexed object, toObject with fallback for non-array-like ES3 strings
var IObject = __webpack_require__(33);
var defined = __webpack_require__(32);
module.exports = function (it) {
  return IObject(defined(it));
};


/***/ }),
/* 24 */
/***/ (function(module, exports, __webpack_require__) {

// 7.1.15 ToLength
var toInteger = __webpack_require__(34);
var min = Math.min;
module.exports = function (it) {
  return it > 0 ? min(toInteger(it), 0x1fffffffffffff) : 0; // pow(2, 53) - 1 == 9007199254740991
};


/***/ }),
/* 25 */
/***/ (function(module, exports, __webpack_require__) {

var def = __webpack_require__(5).f;
var has = __webpack_require__(14);
var TAG = __webpack_require__(2)('toStringTag');

module.exports = function (it, tag, stat) {
  if (it && !has(it = stat ? it : it.prototype, TAG)) def(it, TAG, { configurable: true, value: tag });
};


/***/ }),
/* 26 */
/***/ (function(module, exports, __webpack_require__) {

// getting tag from 19.1.3.6 Object.prototype.toString()
var cof = __webpack_require__(15);
var TAG = __webpack_require__(2)('toStringTag');
// ES3 wrong here
var ARG = cof(function () { return arguments; }()) == 'Arguments';

// fallback for IE11 Script Access Denied error
var tryGet = function (it, key) {
  try {
    return it[key];
  } catch (e) { /* empty */ }
};

module.exports = function (it) {
  var O, T, B;
  return it === undefined ? 'Undefined' : it === null ? 'Null'
    // @@toStringTag case
    : typeof (T = tryGet(O = Object(it), TAG)) == 'string' ? T
    // builtinTag case
    : ARG ? cof(O)
    // ES3 arguments fallback
    : (B = cof(O)) == 'Object' && typeof O.callee == 'function' ? 'Arguments' : B;
};


/***/ }),
/* 27 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(112), __esModule: true };

/***/ }),
/* 28 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(120), __esModule: true };

/***/ }),
/* 29 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


exports.__esModule = true;

exports["default"] = function (instance, Constructor) {
  if (!(instance instanceof Constructor)) {
    throw new TypeError("Cannot call a class as a function");
  }
};

/***/ }),
/* 30 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


exports.__esModule = true;

var _defineProperty = __webpack_require__(124);

var _defineProperty2 = _interopRequireDefault(_defineProperty);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

exports["default"] = function () {
  function defineProperties(target, props) {
    for (var i = 0; i < props.length; i++) {
      var descriptor = props[i];
      descriptor.enumerable = descriptor.enumerable || false;
      descriptor.configurable = true;
      if ("value" in descriptor) descriptor.writable = true;
      (0, _defineProperty2["default"])(target, descriptor.key, descriptor);
    }
  }

  return function (Constructor, protoProps, staticProps) {
    if (protoProps) defineProperties(Constructor.prototype, protoProps);
    if (staticProps) defineProperties(Constructor, staticProps);
    return Constructor;
  };
}();

/***/ }),
/* 31 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.JSONDecode = exports.JSONEncode = exports.base64Decode = exports.base64Encode = exports.objectToMap = exports.mapToObject = exports.times = exports.isValidDate = exports.isUndefined = exports.isUuid = exports.isString = exports.isObject = exports.enumerate = exports.uuid = undefined;

var _stringify = __webpack_require__(136);

var _stringify2 = _interopRequireDefault(_stringify);

var _keys = __webpack_require__(21);

var _keys2 = _interopRequireDefault(_keys);

var _map = __webpack_require__(17);

var _map2 = _interopRequireDefault(_map);

var _slicedToArray2 = __webpack_require__(20);

var _slicedToArray3 = _interopRequireDefault(_slicedToArray2);

var _is = __webpack_require__(50);

var _is2 = _interopRequireDefault(_is);

var _regenerator = __webpack_require__(138);

var _regenerator2 = _interopRequireDefault(_regenerator);

var _getIterator2 = __webpack_require__(27);

var _getIterator3 = _interopRequireDefault(_getIterator2);

var _b2a = __webpack_require__(141);

var b2a = _interopRequireWildcard(_b2a);

function _interopRequireWildcard(obj) { if (obj && obj.__esModule) { return obj; } else { var newObj = {}; if (obj != null) { for (var key in obj) { if (Object.prototype.hasOwnProperty.call(obj, key)) newObj[key] = obj[key]; } } newObj["default"] = obj; return newObj; } }

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

if (!window.btoa) {
    Object.defineProperty(window, 'btoa', {
        value: b2a.btoa
    });
}
if (!window.atob) {
    Object.defineProperty(window, 'atob', {
        value: b2a.atob
    });
}

var uuid = exports.uuid = function uuid() {
    var d = new Date().getTime();
    var _uuid = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function (c) {
        var r = (d + Math.random() * 16) % 16 | 0;
        d = Math.floor(d / 16);
        return (c === 'x' ? r : r & 0x7 | 0x8).toString(16);
    });

    return _uuid;
};

var enumerate = /*#__PURE__*/exports.enumerate = _regenerator2["default"].mark(function enumerate(iterable) {
    var i, _iteratorNormalCompletion, _didIteratorError, _iteratorError, _iterator, _step, x;

    return _regenerator2["default"].wrap(function enumerate$(_context) {
        while (1) {
            switch (_context.prev = _context.next) {
                case 0:
                    i = 0;
                    _iteratorNormalCompletion = true;
                    _didIteratorError = false;
                    _iteratorError = undefined;
                    _context.prev = 4;
                    _iterator = (0, _getIterator3["default"])(iterable);

                case 6:
                    if (_iteratorNormalCompletion = (_step = _iterator.next()).done) {
                        _context.next = 14;
                        break;
                    }

                    x = _step.value;
                    _context.next = 10;
                    return [i, x];

                case 10:
                    i++;

                case 11:
                    _iteratorNormalCompletion = true;
                    _context.next = 6;
                    break;

                case 14:
                    _context.next = 20;
                    break;

                case 16:
                    _context.prev = 16;
                    _context.t0 = _context['catch'](4);
                    _didIteratorError = true;
                    _iteratorError = _context.t0;

                case 20:
                    _context.prev = 20;
                    _context.prev = 21;

                    if (!_iteratorNormalCompletion && _iterator["return"]) {
                        _iterator["return"]();
                    }

                case 23:
                    _context.prev = 23;

                    if (!_didIteratorError) {
                        _context.next = 26;
                        break;
                    }

                    throw _iteratorError;

                case 26:
                    return _context.finish(23);

                case 27:
                    return _context.finish(20);

                case 28:
                case 'end':
                    return _context.stop();
            }
        }
    }, enumerate, this, [[4, 16, 20, 28], [21,, 23, 27]]);
});

var isObject = exports.isObject = function isObject(obj) {
    return (0, _is2["default"])(obj, Object(obj));
};
var isString = exports.isString = function isString(obj) {
    return (0, _is2["default"])(Object.prototype.toString.call(obj), '[object String]');
};
var isUuid = exports.isUuid = function isUuid(str) {
    return (/^[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}$/.test(str)
    );
};
var isUndefined = exports.isUndefined = function isUndefined(obj) {
    return (0, _is2["default"])(obj, void 0);
};

var isEpoch = function isEpoch(str) {
    return (/^(\d{10}|\d{13,})$/.test(str)
    );
};
var isIsoString = function isIsoString(str) {
    return (/^\d{4}-[01]\d-[0-3]/.test(str)
    );
};
var isValidDate = exports.isValidDate = function isValidDate(str) {
    return isEpoch(str) || isIsoString(str);
};

var times = exports.times = function times(n, fn) {
    while (n-- > 0) {
        fn();
    }
};

var mapToObject = exports.mapToObject = function mapToObject(map) {
    var obj = {};
    var _iteratorNormalCompletion2 = true;
    var _didIteratorError2 = false;
    var _iteratorError2 = undefined;

    try {
        for (var _iterator2 = (0, _getIterator3["default"])(map), _step2; !(_iteratorNormalCompletion2 = (_step2 = _iterator2.next()).done); _iteratorNormalCompletion2 = true) {
            var _ref = _step2.value;

            var _ref2 = (0, _slicedToArray3["default"])(_ref, 2);

            var key = _ref2[0];
            var value = _ref2[1];

            obj[key] = value;
        }
    } catch (err) {
        _didIteratorError2 = true;
        _iteratorError2 = err;
    } finally {
        try {
            if (!_iteratorNormalCompletion2 && _iterator2["return"]) {
                _iterator2["return"]();
            }
        } finally {
            if (_didIteratorError2) {
                throw _iteratorError2;
            }
        }
    }

    return obj;
};

var objectToMap = exports.objectToMap = function objectToMap(obj) {
    return new _map2["default"]((0, _keys2["default"])(obj).map(function (key) {
        return [key, obj[key]];
    }));
};

var base64Encode = exports.base64Encode = function base64Encode(str) {
    return btoa(encodeURIComponent(str).replace(/%([0-9A-F]{2})/g, function (match, p1) {
        return String.fromCharCode(parseInt(p1, 16));
    }));
};

var base64Decode = exports.base64Decode = function base64Decode(str) {
    return decodeURIComponent(Array.prototype.map.call(atob(str), function (c) {
        return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
    }).join(''));
};

var JSONEncode = exports.JSONEncode = _stringify2["default"];
var JSONDecode = exports.JSONDecode = JSON.parse;

/***/ }),
/* 32 */
/***/ (function(module, exports) {

// 7.2.1 RequireObjectCoercible(argument)
module.exports = function (it) {
  if (it == undefined) throw TypeError("Can't call method on  " + it);
  return it;
};


/***/ }),
/* 33 */
/***/ (function(module, exports, __webpack_require__) {

// fallback for non-array-like ES3 and non-enumerable old V8 strings
var cof = __webpack_require__(15);
// eslint-disable-next-line no-prototype-builtins
module.exports = Object('z').propertyIsEnumerable(0) ? Object : function (it) {
  return cof(it) == 'String' ? it.split('') : Object(it);
};


/***/ }),
/* 34 */
/***/ (function(module, exports) {

// 7.1.4 ToInteger
var ceil = Math.ceil;
var floor = Math.floor;
module.exports = function (it) {
  return isNaN(it = +it) ? 0 : (it > 0 ? floor : ceil)(it);
};


/***/ }),
/* 35 */
/***/ (function(module, exports, __webpack_require__) {

var shared = __webpack_require__(47)('keys');
var uid = __webpack_require__(36);
module.exports = function (key) {
  return shared[key] || (shared[key] = uid(key));
};


/***/ }),
/* 36 */
/***/ (function(module, exports) {

var id = 0;
var px = Math.random();
module.exports = function (key) {
  return 'Symbol('.concat(key === undefined ? '' : key, ')_', (++id + px).toString(36));
};


/***/ }),
/* 37 */
/***/ (function(module, exports, __webpack_require__) {

var isObject = __webpack_require__(4);
var document = __webpack_require__(3).document;
// typeof document.createElement is 'object' in old IE
var is = isObject(document) && isObject(document.createElement);
module.exports = function (it) {
  return is ? document.createElement(it) : {};
};


/***/ }),
/* 38 */
/***/ (function(module, exports) {

module.exports = function (bitmap, value) {
  return {
    enumerable: !(bitmap & 1),
    configurable: !(bitmap & 2),
    writable: !(bitmap & 4),
    value: value
  };
};


/***/ }),
/* 39 */
/***/ (function(module, exports) {



/***/ }),
/* 40 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var LIBRARY = __webpack_require__(51);
var $export = __webpack_require__(1);
var redefine = __webpack_require__(94);
var hide = __webpack_require__(9);
var has = __webpack_require__(14);
var Iterators = __webpack_require__(12);
var $iterCreate = __webpack_require__(95);
var setToStringTag = __webpack_require__(25);
var getPrototypeOf = __webpack_require__(97);
var ITERATOR = __webpack_require__(2)('iterator');
var BUGGY = !([].keys && 'next' in [].keys()); // Safari has buggy iterators w/o `next`
var FF_ITERATOR = '@@iterator';
var KEYS = 'keys';
var VALUES = 'values';

var returnThis = function () { return this; };

module.exports = function (Base, NAME, Constructor, next, DEFAULT, IS_SET, FORCED) {
  $iterCreate(Constructor, NAME, next);
  var getMethod = function (kind) {
    if (!BUGGY && kind in proto) return proto[kind];
    switch (kind) {
      case KEYS: return function keys() { return new Constructor(this, kind); };
      case VALUES: return function values() { return new Constructor(this, kind); };
    } return function entries() { return new Constructor(this, kind); };
  };
  var TAG = NAME + ' Iterator';
  var DEF_VALUES = DEFAULT == VALUES;
  var VALUES_BUG = false;
  var proto = Base.prototype;
  var $native = proto[ITERATOR] || proto[FF_ITERATOR] || DEFAULT && proto[DEFAULT];
  var $default = $native || getMethod(DEFAULT);
  var $entries = DEFAULT ? !DEF_VALUES ? $default : getMethod('entries') : undefined;
  var $anyNative = NAME == 'Array' ? proto.entries || $native : $native;
  var methods, key, IteratorPrototype;
  // Fix native
  if ($anyNative) {
    IteratorPrototype = getPrototypeOf($anyNative.call(new Base()));
    if (IteratorPrototype !== Object.prototype && IteratorPrototype.next) {
      // Set @@toStringTag to native iterators
      setToStringTag(IteratorPrototype, TAG, true);
      // fix for some old engines
      if (!LIBRARY && !has(IteratorPrototype, ITERATOR)) hide(IteratorPrototype, ITERATOR, returnThis);
    }
  }
  // fix Array#{values, @@iterator}.name in V8 / FF
  if (DEF_VALUES && $native && $native.name !== VALUES) {
    VALUES_BUG = true;
    $default = function values() { return $native.call(this); };
  }
  // Define iterator
  if ((!LIBRARY || FORCED) && (BUGGY || VALUES_BUG || !proto[ITERATOR])) {
    hide(proto, ITERATOR, $default);
  }
  // Plug for library
  Iterators[NAME] = $default;
  Iterators[TAG] = returnThis;
  if (DEFAULT) {
    methods = {
      values: DEF_VALUES ? $default : getMethod(VALUES),
      keys: IS_SET ? $default : getMethod(KEYS),
      entries: $entries
    };
    if (FORCED) for (key in methods) {
      if (!(key in proto)) redefine(proto, key, methods[key]);
    } else $export($export.P + $export.F * (BUGGY || VALUES_BUG), NAME, methods);
  }
  return methods;
};


/***/ }),
/* 41 */
/***/ (function(module, exports, __webpack_require__) {

var hide = __webpack_require__(9);
module.exports = function (target, src, safe) {
  for (var key in src) {
    if (safe && target[key]) target[key] = src[key];
    else hide(target, key, src[key]);
  } return target;
};


/***/ }),
/* 42 */
/***/ (function(module, exports) {

module.exports = function (it, Constructor, name, forbiddenField) {
  if (!(it instanceof Constructor) || (forbiddenField !== undefined && forbiddenField in it)) {
    throw TypeError(name + ': incorrect invocation!');
  } return it;
};


/***/ }),
/* 43 */
/***/ (function(module, exports, __webpack_require__) {

var classof = __webpack_require__(26);
var ITERATOR = __webpack_require__(2)('iterator');
var Iterators = __webpack_require__(12);
module.exports = __webpack_require__(0).getIteratorMethod = function (it) {
  if (it != undefined) return it[ITERATOR]
    || it['@@iterator']
    || Iterators[classof(it)];
};


/***/ }),
/* 44 */
/***/ (function(module, exports, __webpack_require__) {

var isObject = __webpack_require__(4);
module.exports = function (it, TYPE) {
  if (!isObject(it) || it._t !== TYPE) throw TypeError('Incompatible receiver, ' + TYPE + ' required!');
  return it;
};


/***/ }),
/* 45 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

// 25.4.1.5 NewPromiseCapability(C)
var aFunction = __webpack_require__(16);

function PromiseCapability(C) {
  var resolve, reject;
  this.promise = new C(function ($$resolve, $$reject) {
    if (resolve !== undefined || reject !== undefined) throw TypeError('Bad Promise constructor');
    resolve = $$resolve;
    reject = $$reject;
  });
  this.resolve = aFunction(resolve);
  this.reject = aFunction(reject);
}

module.exports.f = function (C) {
  return new PromiseCapability(C);
};


/***/ }),
/* 46 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.buildQueryString = exports.parseQueryString = undefined;

var _slicedToArray2 = __webpack_require__(20);

var _slicedToArray3 = _interopRequireDefault(_slicedToArray2);

var _map = __webpack_require__(17);

var _map2 = _interopRequireDefault(_map);

var _common = __webpack_require__(31);

var common = _interopRequireWildcard(_common);

function _interopRequireWildcard(obj) { if (obj && obj.__esModule) { return obj; } else { var newObj = {}; if (obj != null) { for (var key in obj) { if (Object.prototype.hasOwnProperty.call(obj, key)) newObj[key] = obj[key]; } } newObj["default"] = obj; return newObj; } }

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var parseQueryString = exports.parseQueryString = function parseQueryString(queryString) {
    var qs = queryString || window.location.search.substring(1);
    var results = new _map2["default"]();

    qs.split('&').forEach(function (query) {
        var _query$split = query.split('='),
            _query$split2 = (0, _slicedToArray3["default"])(_query$split, 2),
            key = _query$split2[0],
            value = _query$split2[1];

        results.set(decodeURIComponent(key), decodeURIComponent(value));
    });

    return results;
};

var buildQueryString = exports.buildQueryString = function buildQueryString(query) {
    var siteId = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : null;


    var queryArray = [];

    if (query) {
        query.forEach(function (value, key, _array) {
            if (value === null || typeof value === 'undefined' || value === '') return;

            var k = encodeURIComponent(key);
            var v = value;
            if (common.isObject(v)) {
                v = encodeURIComponent(common.JSONEncode(value));
            } else {
                v = encodeURIComponent(value);
            }
            queryArray.push(k + '=' + v);
        });
    }
    if (siteId) {
        queryArray.push('site_id=' + siteId);
    }

    return queryArray.join('&');
};

/***/ }),
/* 47 */
/***/ (function(module, exports, __webpack_require__) {

var global = __webpack_require__(3);
var SHARED = '__core-js_shared__';
var store = global[SHARED] || (global[SHARED] = {});
module.exports = function (key) {
  return store[key] || (store[key] = {});
};


/***/ }),
/* 48 */
/***/ (function(module, exports) {

// IE 8- don't enum bug keys
module.exports = (
  'constructor,hasOwnProperty,isPrototypeOf,propertyIsEnumerable,toLocaleString,toString,valueOf'
).split(',');


/***/ }),
/* 49 */
/***/ (function(module, exports) {

exports.f = {}.propertyIsEnumerable;


/***/ }),
/* 50 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(89), __esModule: true };

/***/ }),
/* 51 */
/***/ (function(module, exports) {

module.exports = true;


/***/ }),
/* 52 */
/***/ (function(module, exports, __webpack_require__) {

// 19.1.2.2 / 15.2.3.5 Object.create(O [, Properties])
var anObject = __webpack_require__(7);
var dPs = __webpack_require__(96);
var enumBugKeys = __webpack_require__(48);
var IE_PROTO = __webpack_require__(35)('IE_PROTO');
var Empty = function () { /* empty */ };
var PROTOTYPE = 'prototype';

// Create object with fake `null` prototype: use iframe Object with cleared prototype
var createDict = function () {
  // Thrash, waste and sodomy: IE GC bug
  var iframe = __webpack_require__(37)('iframe');
  var i = enumBugKeys.length;
  var lt = '<';
  var gt = '>';
  var iframeDocument;
  iframe.style.display = 'none';
  __webpack_require__(53).appendChild(iframe);
  iframe.src = 'javascript:'; // eslint-disable-line no-script-url
  // createDict = iframe.contentWindow.Object;
  // html.removeChild(iframe);
  iframeDocument = iframe.contentWindow.document;
  iframeDocument.open();
  iframeDocument.write(lt + 'script' + gt + 'document.F=Object' + lt + '/script' + gt);
  iframeDocument.close();
  createDict = iframeDocument.F;
  while (i--) delete createDict[PROTOTYPE][enumBugKeys[i]];
  return createDict();
};

module.exports = Object.create || function create(O, Properties) {
  var result;
  if (O !== null) {
    Empty[PROTOTYPE] = anObject(O);
    result = new Empty();
    Empty[PROTOTYPE] = null;
    // add "__proto__" for Object.getPrototypeOf polyfill
    result[IE_PROTO] = O;
  } else result = createDict();
  return Properties === undefined ? result : dPs(result, Properties);
};


/***/ }),
/* 53 */
/***/ (function(module, exports, __webpack_require__) {

var document = __webpack_require__(3).document;
module.exports = document && document.documentElement;


/***/ }),
/* 54 */
/***/ (function(module, exports) {

module.exports = function (done, value) {
  return { value: value, done: !!done };
};


/***/ }),
/* 55 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var dP = __webpack_require__(5).f;
var create = __webpack_require__(52);
var redefineAll = __webpack_require__(41);
var ctx = __webpack_require__(6);
var anInstance = __webpack_require__(42);
var forOf = __webpack_require__(19);
var $iterDefine = __webpack_require__(40);
var step = __webpack_require__(54);
var setSpecies = __webpack_require__(58);
var DESCRIPTORS = __webpack_require__(8);
var fastKey = __webpack_require__(59).fastKey;
var validate = __webpack_require__(44);
var SIZE = DESCRIPTORS ? '_s' : 'size';

var getEntry = function (that, key) {
  // fast case
  var index = fastKey(key);
  var entry;
  if (index !== 'F') return that._i[index];
  // frozen object case
  for (entry = that._f; entry; entry = entry.n) {
    if (entry.k == key) return entry;
  }
};

module.exports = {
  getConstructor: function (wrapper, NAME, IS_MAP, ADDER) {
    var C = wrapper(function (that, iterable) {
      anInstance(that, C, NAME, '_i');
      that._t = NAME;         // collection type
      that._i = create(null); // index
      that._f = undefined;    // first entry
      that._l = undefined;    // last entry
      that[SIZE] = 0;         // size
      if (iterable != undefined) forOf(iterable, IS_MAP, that[ADDER], that);
    });
    redefineAll(C.prototype, {
      // 23.1.3.1 Map.prototype.clear()
      // 23.2.3.2 Set.prototype.clear()
      clear: function clear() {
        for (var that = validate(this, NAME), data = that._i, entry = that._f; entry; entry = entry.n) {
          entry.r = true;
          if (entry.p) entry.p = entry.p.n = undefined;
          delete data[entry.i];
        }
        that._f = that._l = undefined;
        that[SIZE] = 0;
      },
      // 23.1.3.3 Map.prototype.delete(key)
      // 23.2.3.4 Set.prototype.delete(value)
      'delete': function (key) {
        var that = validate(this, NAME);
        var entry = getEntry(that, key);
        if (entry) {
          var next = entry.n;
          var prev = entry.p;
          delete that._i[entry.i];
          entry.r = true;
          if (prev) prev.n = next;
          if (next) next.p = prev;
          if (that._f == entry) that._f = next;
          if (that._l == entry) that._l = prev;
          that[SIZE]--;
        } return !!entry;
      },
      // 23.2.3.6 Set.prototype.forEach(callbackfn, thisArg = undefined)
      // 23.1.3.5 Map.prototype.forEach(callbackfn, thisArg = undefined)
      forEach: function forEach(callbackfn /* , that = undefined */) {
        validate(this, NAME);
        var f = ctx(callbackfn, arguments.length > 1 ? arguments[1] : undefined, 3);
        var entry;
        while (entry = entry ? entry.n : this._f) {
          f(entry.v, entry.k, this);
          // revert to the last existing entry
          while (entry && entry.r) entry = entry.p;
        }
      },
      // 23.1.3.7 Map.prototype.has(key)
      // 23.2.3.7 Set.prototype.has(value)
      has: function has(key) {
        return !!getEntry(validate(this, NAME), key);
      }
    });
    if (DESCRIPTORS) dP(C.prototype, 'size', {
      get: function () {
        return validate(this, NAME)[SIZE];
      }
    });
    return C;
  },
  def: function (that, key, value) {
    var entry = getEntry(that, key);
    var prev, index;
    // change existing entry
    if (entry) {
      entry.v = value;
    // create new entry
    } else {
      that._l = entry = {
        i: index = fastKey(key, true), // <- index
        k: key,                        // <- key
        v: value,                      // <- value
        p: prev = that._l,             // <- previous entry
        n: undefined,                  // <- next entry
        r: false                       // <- removed
      };
      if (!that._f) that._f = entry;
      if (prev) prev.n = entry;
      that[SIZE]++;
      // add to index
      if (index !== 'F') that._i[index] = entry;
    } return that;
  },
  getEntry: getEntry,
  setStrong: function (C, NAME, IS_MAP) {
    // add .keys, .values, .entries, [@@iterator]
    // 23.1.3.4, 23.1.3.8, 23.1.3.11, 23.1.3.12, 23.2.3.5, 23.2.3.8, 23.2.3.10, 23.2.3.11
    $iterDefine(C, NAME, function (iterated, kind) {
      this._t = validate(iterated, NAME); // target
      this._k = kind;                     // kind
      this._l = undefined;                // previous
    }, function () {
      var that = this;
      var kind = that._k;
      var entry = that._l;
      // revert to the last existing entry
      while (entry && entry.r) entry = entry.p;
      // get next entry
      if (!that._t || !(that._l = entry = entry ? entry.n : that._t._f)) {
        // or finish the iteration
        that._t = undefined;
        return step(1);
      }
      // return step by kind
      if (kind == 'keys') return step(0, entry.k);
      if (kind == 'values') return step(0, entry.v);
      return step(0, [entry.k, entry.v]);
    }, IS_MAP ? 'entries' : 'values', !IS_MAP, true);

    // add [@@species], 23.1.2.2, 23.2.2.2
    setSpecies(NAME);
  }
};


/***/ }),
/* 56 */
/***/ (function(module, exports, __webpack_require__) {

// call something on iterator step with safe closing on error
var anObject = __webpack_require__(7);
module.exports = function (iterator, fn, value, entries) {
  try {
    return entries ? fn(anObject(value)[0], value[1]) : fn(value);
  // 7.4.6 IteratorClose(iterator, completion)
  } catch (e) {
    var ret = iterator['return'];
    if (ret !== undefined) anObject(ret.call(iterator));
    throw e;
  }
};


/***/ }),
/* 57 */
/***/ (function(module, exports, __webpack_require__) {

// check on default Array iterator
var Iterators = __webpack_require__(12);
var ITERATOR = __webpack_require__(2)('iterator');
var ArrayProto = Array.prototype;

module.exports = function (it) {
  return it !== undefined && (Iterators.Array === it || ArrayProto[ITERATOR] === it);
};


/***/ }),
/* 58 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var global = __webpack_require__(3);
var core = __webpack_require__(0);
var dP = __webpack_require__(5);
var DESCRIPTORS = __webpack_require__(8);
var SPECIES = __webpack_require__(2)('species');

module.exports = function (KEY) {
  var C = typeof core[KEY] == 'function' ? core[KEY] : global[KEY];
  if (DESCRIPTORS && C && !C[SPECIES]) dP.f(C, SPECIES, {
    configurable: true,
    get: function () { return this; }
  });
};


/***/ }),
/* 59 */
/***/ (function(module, exports, __webpack_require__) {

var META = __webpack_require__(36)('meta');
var isObject = __webpack_require__(4);
var has = __webpack_require__(14);
var setDesc = __webpack_require__(5).f;
var id = 0;
var isExtensible = Object.isExtensible || function () {
  return true;
};
var FREEZE = !__webpack_require__(10)(function () {
  return isExtensible(Object.preventExtensions({}));
});
var setMeta = function (it) {
  setDesc(it, META, { value: {
    i: 'O' + ++id, // object ID
    w: {}          // weak collections IDs
  } });
};
var fastKey = function (it, create) {
  // return primitive with prefix
  if (!isObject(it)) return typeof it == 'symbol' ? it : (typeof it == 'string' ? 'S' : 'P') + it;
  if (!has(it, META)) {
    // can't set metadata to uncaught frozen object
    if (!isExtensible(it)) return 'F';
    // not necessary to add metadata
    if (!create) return 'E';
    // add missing metadata
    setMeta(it);
  // return object ID
  } return it[META].i;
};
var getWeak = function (it, create) {
  if (!has(it, META)) {
    // can't set metadata to uncaught frozen object
    if (!isExtensible(it)) return true;
    // not necessary to add metadata
    if (!create) return false;
    // add missing metadata
    setMeta(it);
  // return hash weak collections IDs
  } return it[META].w;
};
// add metadata on freeze-family methods calling
var onFreeze = function (it) {
  if (FREEZE && meta.NEED && isExtensible(it) && !has(it, META)) setMeta(it);
  return it;
};
var meta = module.exports = {
  KEY: META,
  NEED: false,
  fastKey: fastKey,
  getWeak: getWeak,
  onFreeze: onFreeze
};


/***/ }),
/* 60 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var global = __webpack_require__(3);
var $export = __webpack_require__(1);
var meta = __webpack_require__(59);
var fails = __webpack_require__(10);
var hide = __webpack_require__(9);
var redefineAll = __webpack_require__(41);
var forOf = __webpack_require__(19);
var anInstance = __webpack_require__(42);
var isObject = __webpack_require__(4);
var setToStringTag = __webpack_require__(25);
var dP = __webpack_require__(5).f;
var each = __webpack_require__(101)(0);
var DESCRIPTORS = __webpack_require__(8);

module.exports = function (NAME, wrapper, methods, common, IS_MAP, IS_WEAK) {
  var Base = global[NAME];
  var C = Base;
  var ADDER = IS_MAP ? 'set' : 'add';
  var proto = C && C.prototype;
  var O = {};
  if (!DESCRIPTORS || typeof C != 'function' || !(IS_WEAK || proto.forEach && !fails(function () {
    new C().entries().next();
  }))) {
    // create collection constructor
    C = common.getConstructor(wrapper, NAME, IS_MAP, ADDER);
    redefineAll(C.prototype, methods);
    meta.NEED = true;
  } else {
    C = wrapper(function (target, iterable) {
      anInstance(target, C, NAME, '_c');
      target._c = new Base();
      if (iterable != undefined) forOf(iterable, IS_MAP, target[ADDER], target);
    });
    each('add,clear,delete,forEach,get,has,set,keys,values,entries,toJSON'.split(','), function (KEY) {
      var IS_ADDER = KEY == 'add' || KEY == 'set';
      if (KEY in proto && !(IS_WEAK && KEY == 'clear')) hide(C.prototype, KEY, function (a, b) {
        anInstance(this, C, KEY);
        if (!IS_ADDER && IS_WEAK && !isObject(a)) return KEY == 'get' ? undefined : false;
        var result = this._c[KEY](a === 0 ? 0 : a, b);
        return IS_ADDER ? this : result;
      });
    });
    IS_WEAK || dP(C.prototype, 'size', {
      get: function () {
        return this._c.size;
      }
    });
  }

  setToStringTag(C, NAME);

  O[NAME] = C;
  $export($export.G + $export.W + $export.F, O);

  if (!IS_WEAK) common.setStrong(C, NAME, IS_MAP);

  return C;
};


/***/ }),
/* 61 */
/***/ (function(module, exports, __webpack_require__) {

// https://github.com/DavidBruant/Map-Set.prototype.toJSON
var classof = __webpack_require__(26);
var from = __webpack_require__(106);
module.exports = function (NAME) {
  return function toJSON() {
    if (classof(this) != NAME) throw TypeError(NAME + "#toJSON isn't generic");
    return from(this);
  };
};


/***/ }),
/* 62 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

// https://tc39.github.io/proposal-setmap-offrom/
var $export = __webpack_require__(1);

module.exports = function (COLLECTION) {
  $export($export.S, COLLECTION, { of: function of() {
    var length = arguments.length;
    var A = Array(length);
    while (length--) A[length] = arguments[length];
    return new this(A);
  } });
};


/***/ }),
/* 63 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

// https://tc39.github.io/proposal-setmap-offrom/
var $export = __webpack_require__(1);
var aFunction = __webpack_require__(16);
var ctx = __webpack_require__(6);
var forOf = __webpack_require__(19);

module.exports = function (COLLECTION) {
  $export($export.S, COLLECTION, { from: function from(source /* , mapFn, thisArg */) {
    var mapFn = arguments[1];
    var mapping, A, n, cb;
    aFunction(this);
    mapping = mapFn !== undefined;
    if (mapping) aFunction(mapFn);
    if (source == undefined) return new this();
    A = [];
    if (mapping) {
      n = 0;
      cb = ctx(mapFn, arguments[2], 2);
      forOf(source, false, function (nextItem) {
        A.push(cb(nextItem, n++));
      });
    } else {
      forOf(source, false, A.push, A);
    }
    return new this(A);
  } });
};


/***/ }),
/* 64 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(114), __esModule: true };

/***/ }),
/* 65 */
/***/ (function(module, exports, __webpack_require__) {

// 7.3.20 SpeciesConstructor(O, defaultConstructor)
var anObject = __webpack_require__(7);
var aFunction = __webpack_require__(16);
var SPECIES = __webpack_require__(2)('species');
module.exports = function (O, D) {
  var C = anObject(O).constructor;
  var S;
  return C === undefined || (S = anObject(C)[SPECIES]) == undefined ? D : aFunction(S);
};


/***/ }),
/* 66 */
/***/ (function(module, exports, __webpack_require__) {

var ctx = __webpack_require__(6);
var invoke = __webpack_require__(116);
var html = __webpack_require__(53);
var cel = __webpack_require__(37);
var global = __webpack_require__(3);
var process = global.process;
var setTask = global.setImmediate;
var clearTask = global.clearImmediate;
var MessageChannel = global.MessageChannel;
var Dispatch = global.Dispatch;
var counter = 0;
var queue = {};
var ONREADYSTATECHANGE = 'onreadystatechange';
var defer, channel, port;
var run = function () {
  var id = +this;
  // eslint-disable-next-line no-prototype-builtins
  if (queue.hasOwnProperty(id)) {
    var fn = queue[id];
    delete queue[id];
    fn();
  }
};
var listener = function (event) {
  run.call(event.data);
};
// Node.js 0.9+ & IE10+ has setImmediate, otherwise:
if (!setTask || !clearTask) {
  setTask = function setImmediate(fn) {
    var args = [];
    var i = 1;
    while (arguments.length > i) args.push(arguments[i++]);
    queue[++counter] = function () {
      // eslint-disable-next-line no-new-func
      invoke(typeof fn == 'function' ? fn : Function(fn), args);
    };
    defer(counter);
    return counter;
  };
  clearTask = function clearImmediate(id) {
    delete queue[id];
  };
  // Node.js 0.8-
  if (__webpack_require__(15)(process) == 'process') {
    defer = function (id) {
      process.nextTick(ctx(run, id, 1));
    };
  // Sphere (JS game engine) Dispatch API
  } else if (Dispatch && Dispatch.now) {
    defer = function (id) {
      Dispatch.now(ctx(run, id, 1));
    };
  // Browsers with MessageChannel, includes WebWorkers
  } else if (MessageChannel) {
    channel = new MessageChannel();
    port = channel.port2;
    channel.port1.onmessage = listener;
    defer = ctx(port.postMessage, port, 1);
  // Browsers with postMessage, skip WebWorkers
  // IE8 has postMessage, but it's sync & typeof its postMessage is 'object'
  } else if (global.addEventListener && typeof postMessage == 'function' && !global.importScripts) {
    defer = function (id) {
      global.postMessage(id + '', '*');
    };
    global.addEventListener('message', listener, false);
  // IE8-
  } else if (ONREADYSTATECHANGE in cel('script')) {
    defer = function (id) {
      html.appendChild(cel('script'))[ONREADYSTATECHANGE] = function () {
        html.removeChild(this);
        run.call(id);
      };
    };
  // Rest old browsers
  } else {
    defer = function (id) {
      setTimeout(ctx(run, id, 1), 0);
    };
  }
}
module.exports = {
  set: setTask,
  clear: clearTask
};


/***/ }),
/* 67 */
/***/ (function(module, exports) {

module.exports = function (exec) {
  try {
    return { e: false, v: exec() };
  } catch (e) {
    return { e: true, v: e };
  }
};


/***/ }),
/* 68 */
/***/ (function(module, exports, __webpack_require__) {

var anObject = __webpack_require__(7);
var isObject = __webpack_require__(4);
var newPromiseCapability = __webpack_require__(45);

module.exports = function (C, x) {
  anObject(C);
  if (isObject(x) && x.constructor === C) return x;
  var promiseCapability = newPromiseCapability.f(C);
  var resolve = promiseCapability.resolve;
  resolve(x);
  return promiseCapability.promise;
};


/***/ }),
/* 69 */
/***/ (function(module, exports, __webpack_require__) {

var ITERATOR = __webpack_require__(2)('iterator');
var SAFE_CLOSING = false;

try {
  var riter = [7][ITERATOR]();
  riter['return'] = function () { SAFE_CLOSING = true; };
  // eslint-disable-next-line no-throw-literal
  Array.from(riter, function () { throw 2; });
} catch (e) { /* empty */ }

module.exports = function (exec, skipClosing) {
  if (!skipClosing && !SAFE_CLOSING) return false;
  var safe = false;
  try {
    var arr = [7];
    var iter = arr[ITERATOR]();
    iter.next = function () { return { done: safe = true }; };
    arr[ITERATOR] = function () { return iter; };
    exec(arr);
  } catch (e) { /* empty */ }
  return safe;
};


/***/ }),
/* 70 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(128), __esModule: true };

/***/ }),
/* 71 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(131), __esModule: true };

/***/ }),
/* 72 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";
/* eslint no-useless-escape:off */
// TODO: fix regex so we can delete this eslint rule


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.remove = exports.set = exports.get = undefined;

var _slicedToArray2 = __webpack_require__(20);

var _slicedToArray3 = _interopRequireDefault(_slicedToArray2);

var _getIterator2 = __webpack_require__(27);

var _getIterator3 = _interopRequireDefault(_getIterator2);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var getCookie = function getCookie(name) {
    var ca = document.cookie.split(';');
    var _iteratorNormalCompletion = true;
    var _didIteratorError = false;
    var _iteratorError = undefined;

    try {
        for (var _iterator = (0, _getIterator3["default"])(ca), _step; !(_iteratorNormalCompletion = (_step = _iterator.next()).done); _iteratorNormalCompletion = true) {
            var c = _step.value;

            var _c$split = c.split('='),
                _c$split2 = (0, _slicedToArray3["default"])(_c$split, 2),
                key = _c$split2[0],
                value = _c$split2[1];

            key = key.trim();
            if (key && value && key === name) {
                var x = decodeURIComponent(value.trim());
                return x;
            }
        }
    } catch (err) {
        _didIteratorError = true;
        _iteratorError = err;
    } finally {
        try {
            if (!_iteratorNormalCompletion && _iterator["return"]) {
                _iterator["return"]();
            }
        } finally {
            if (_didIteratorError) {
                throw _iteratorError;
            }
        }
    }

    return null;
};

var setCookie = function setCookie(name) {
    var value = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : '';
    var milliseconds = arguments.length > 2 && arguments[2] !== undefined ? arguments[2] : null;
    var crossSubdomain = arguments.length > 3 && arguments[3] !== undefined ? arguments[3] : false;
    var isSecure = arguments.length > 4 && arguments[4] !== undefined ? arguments[4] : false;

    var cookie = name + '=' + encodeURIComponent(value);

    if (milliseconds) {
        var expiresDate = new Date();
        expiresDate.setTime(expiresDate.getTime() + milliseconds);
        cookie += '; expires=' + expiresDate.toGMTString();
    }

    cookie += '; path=/';

    if (crossSubdomain) {
        var matches = document.location.hostname.match(/[a-z0-9][a-z0-9\-]+\.[a-z\.]{2,6}$/i);
        var domain = matches ? matches[0] : '';
        cookie += domain ? '; domain=.' + domain : '';
    }

    if (isSecure) {
        cookie += '; secure';
    }

    document.cookie = cookie;
};

var removeCookie = function removeCookie(name, crossSubdomain) {
    setCookie(name, '', -1, crossSubdomain);
};

exports.get = getCookie;
exports.set = setCookie;
exports.remove = removeCookie;

/***/ }),
/* 73 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(74);
module.exports = __webpack_require__(87);


/***/ }),
/* 74 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


var _keys = __webpack_require__(21);

var _keys2 = _interopRequireDefault(_keys);

var _entries = __webpack_require__(83);

var _entries2 = _interopRequireDefault(_entries);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

/* eslint no-var:off */
/* eslint no-undefined:off */
if (!Array.prototype.fill) {
    Object.defineProperty(Array.prototype, 'fill', {
        value: function value(_value) {

            // Steps 1-2.
            if (this == null) {
                throw new TypeError('this is null or not defined');
            }

            var O = Object(this);

            // Steps 3-5.
            var len = O.length >>> 0;

            // Steps 6-7.
            var start = arguments[1];
            var relativeStart = start >> 0;

            // Step 8.
            var k = relativeStart < 0 ? Math.max(len + relativeStart, 0) : Math.min(relativeStart, len);

            // Steps 9-10.
            var end = arguments[2];
            var relativeEnd = end === undefined ? len : end >> 0;

            // Step 11.
            var final = relativeEnd < 0 ? Math.max(len + relativeEnd, 0) : Math.min(relativeEnd, len);

            // Step 12.
            while (k < final) {
                O[k] = _value;
                k++;
            }

            // Step 13.
            return O;
        }
    });
}

if (!_entries2["default"]) {
    Object.entries = function (obj) {
        var ownProps = (0, _keys2["default"])(obj),
            i = ownProps.length,
            resArray = new Array(i); // preallocate the Array
        while (i--) {
            resArray[i] = [ownProps[i], obj[ownProps[i]]];
        }

        return resArray;
    };
}

/***/ }),
/* 75 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(76);
module.exports = __webpack_require__(0).Object.keys;


/***/ }),
/* 76 */
/***/ (function(module, exports, __webpack_require__) {

// 19.1.2.14 Object.keys(O)
var toObject = __webpack_require__(13);
var $keys = __webpack_require__(22);

__webpack_require__(80)('keys', function () {
  return function keys(it) {
    return $keys(toObject(it));
  };
});


/***/ }),
/* 77 */
/***/ (function(module, exports, __webpack_require__) {

var has = __webpack_require__(14);
var toIObject = __webpack_require__(23);
var arrayIndexOf = __webpack_require__(78)(false);
var IE_PROTO = __webpack_require__(35)('IE_PROTO');

module.exports = function (object, names) {
  var O = toIObject(object);
  var i = 0;
  var result = [];
  var key;
  for (key in O) if (key != IE_PROTO) has(O, key) && result.push(key);
  // Don't enum bug & hidden keys
  while (names.length > i) if (has(O, key = names[i++])) {
    ~arrayIndexOf(result, key) || result.push(key);
  }
  return result;
};


/***/ }),
/* 78 */
/***/ (function(module, exports, __webpack_require__) {

// false -> Array#indexOf
// true  -> Array#includes
var toIObject = __webpack_require__(23);
var toLength = __webpack_require__(24);
var toAbsoluteIndex = __webpack_require__(79);
module.exports = function (IS_INCLUDES) {
  return function ($this, el, fromIndex) {
    var O = toIObject($this);
    var length = toLength(O.length);
    var index = toAbsoluteIndex(fromIndex, length);
    var value;
    // Array#includes uses SameValueZero equality algorithm
    // eslint-disable-next-line no-self-compare
    if (IS_INCLUDES && el != el) while (length > index) {
      value = O[index++];
      // eslint-disable-next-line no-self-compare
      if (value != value) return true;
    // Array#indexOf ignores holes, Array#includes - not
    } else for (;length > index; index++) if (IS_INCLUDES || index in O) {
      if (O[index] === el) return IS_INCLUDES || index || 0;
    } return !IS_INCLUDES && -1;
  };
};


/***/ }),
/* 79 */
/***/ (function(module, exports, __webpack_require__) {

var toInteger = __webpack_require__(34);
var max = Math.max;
var min = Math.min;
module.exports = function (index, length) {
  index = toInteger(index);
  return index < 0 ? max(index + length, 0) : min(index, length);
};


/***/ }),
/* 80 */
/***/ (function(module, exports, __webpack_require__) {

// most Object methods by ES6 should accept primitives
var $export = __webpack_require__(1);
var core = __webpack_require__(0);
var fails = __webpack_require__(10);
module.exports = function (KEY, exec) {
  var fn = (core.Object || {})[KEY] || Object[KEY];
  var exp = {};
  exp[KEY] = exec(fn);
  $export($export.S + $export.F * fails(function () { fn(1); }), 'Object', exp);
};


/***/ }),
/* 81 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = !__webpack_require__(8) && !__webpack_require__(10)(function () {
  return Object.defineProperty(__webpack_require__(37)('div'), 'a', { get: function () { return 7; } }).a != 7;
});


/***/ }),
/* 82 */
/***/ (function(module, exports, __webpack_require__) {

// 7.1.1 ToPrimitive(input [, PreferredType])
var isObject = __webpack_require__(4);
// instead of the ES6 spec version, we didn't implement @@toPrimitive case
// and the second argument - flag - preferred type is a string
module.exports = function (it, S) {
  if (!isObject(it)) return it;
  var fn, val;
  if (S && typeof (fn = it.toString) == 'function' && !isObject(val = fn.call(it))) return val;
  if (typeof (fn = it.valueOf) == 'function' && !isObject(val = fn.call(it))) return val;
  if (!S && typeof (fn = it.toString) == 'function' && !isObject(val = fn.call(it))) return val;
  throw TypeError("Can't convert object to primitive value");
};


/***/ }),
/* 83 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(84), __esModule: true };

/***/ }),
/* 84 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(85);
module.exports = __webpack_require__(0).Object.entries;


/***/ }),
/* 85 */
/***/ (function(module, exports, __webpack_require__) {

// https://github.com/tc39/proposal-object-values-entries
var $export = __webpack_require__(1);
var $entries = __webpack_require__(86)(true);

$export($export.S, 'Object', {
  entries: function entries(it) {
    return $entries(it);
  }
});


/***/ }),
/* 86 */
/***/ (function(module, exports, __webpack_require__) {

var getKeys = __webpack_require__(22);
var toIObject = __webpack_require__(23);
var isEnum = __webpack_require__(49).f;
module.exports = function (isEntries) {
  return function (it) {
    var O = toIObject(it);
    var keys = getKeys(O);
    var length = keys.length;
    var i = 0;
    var result = [];
    var key;
    while (length > i) if (isEnum.call(O, key = keys[i++])) {
      result.push(isEntries ? [key, O[key]] : O[key]);
    } return result;
  };
};


/***/ }),
/* 87 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


var _api = __webpack_require__(88);

_api.BT.create(window._bt);

window._bt.initialize('disqus');

/***/ }),
/* 88 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.BT = undefined;

var _is = __webpack_require__(50);

var _is2 = _interopRequireDefault(_is);

var _keys = __webpack_require__(21);

var _keys2 = _interopRequireDefault(_keys);

var _map = __webpack_require__(17);

var _map2 = _interopRequireDefault(_map);

var _slicedToArray2 = __webpack_require__(20);

var _slicedToArray3 = _interopRequireDefault(_slicedToArray2);

var _promise = __webpack_require__(64);

var _promise2 = _interopRequireDefault(_promise);

var _assign = __webpack_require__(28);

var _assign2 = _interopRequireDefault(_assign);

var _classCallCheck2 = __webpack_require__(29);

var _classCallCheck3 = _interopRequireDefault(_classCallCheck2);

var _createClass2 = __webpack_require__(30);

var _createClass3 = _interopRequireDefault(_createClass2);

var _toConsumableArray2 = __webpack_require__(127);

var _toConsumableArray3 = _interopRequireDefault(_toConsumableArray2);

var _set = __webpack_require__(71);

var _set2 = _interopRequireDefault(_set);

var _common = __webpack_require__(31);

var common = _interopRequireWildcard(_common);

var _webpage = __webpack_require__(142);

var webpage = _interopRequireWildcard(_webpage);

var _config = __webpack_require__(143);

var _console = __webpack_require__(144);

var _identity = __webpack_require__(145);

var _io = __webpack_require__(150);

var _session = __webpack_require__(151);

var _url = __webpack_require__(46);

var _md = __webpack_require__(152);

var _md2 = _interopRequireDefault(_md);

function _interopRequireWildcard(obj) { if (obj && obj.__esModule) { return obj; } else { var newObj = {}; if (obj != null) { for (var key in obj) { if (Object.prototype.hasOwnProperty.call(obj, key)) newObj[key] = obj[key]; } } newObj["default"] = obj; return newObj; } }

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var DEFAULT_VIEW_EVENT = 'viewed';
var DEFAULT_SCROLL_EVENT = 'scrolled';

var EVENT_TYPES = {
    view: new _set2["default"]([DEFAULT_VIEW_EVENT]),
    search: new _set2["default"](['searched']),
    purchase: new _set2["default"](['purchased']),
    cart: new _set2["default"](['updated_cart']),
    signup: new _set2["default"](['started_membership', 'signed_up']),
    scroll: new _set2["default"]([DEFAULT_SCROLL_EVENT]),
    like: new _set2["default"](['liked']),
    share: new _set2["default"](['shared']),
    comment: new _set2["default"](['commented'])
};

var AUGMENT_AS_VIEW = new _set2["default"]([].concat((0, _toConsumableArray3["default"])(EVENT_TYPES.view), (0, _toConsumableArray3["default"])(EVENT_TYPES.scroll), (0, _toConsumableArray3["default"])(EVENT_TYPES.like), (0, _toConsumableArray3["default"])(EVENT_TYPES.share), (0, _toConsumableArray3["default"])(EVENT_TYPES.comment)));

var METHODS = {
    track: 'track',
    identify: '_identify',
    update: 'updateUser',
    clear: 'clear',
    init: 'initialize'
};

var BT = exports.BT = function () {
    function BT(queue) {
        (0, _classCallCheck3["default"])(this, BT);

        this._config = (0, _assign2["default"])({}, _config.CONFIG);

        this._identity = new _identity.Identity();
        this._session = new _session.Session();

        this._console = new _console.Console(console, this._config.debug);

        // variables for testing purposes
        this._pageRequests = [];
        this._pageResponses = [];

        this._queue = queue;
        this._processing = false;
        this._initialized = false;

        // browser/document measurements
        this._maxScrollablePixels = null;
        this._scrollLevelsReached = new _set2["default"]();
        this._setUpScrollTracking();

        this._loadTime = window.performance.now();
    }

    (0, _createClass3["default"])(BT, [{
        key: 'initialize',
        value: function initialize(siteId) {
            var options = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : {};
            var onComplete = arguments.length > 2 && arguments[2] !== undefined ? arguments[2] : function () {};

            if (this._initialized) {
                this._console.log('BT Library already initialized');
                return _promise2["default"].resolve('OK');
            }

            if (!siteId) {
                this._console.error(new Error('Must provide a siteId to initialize()'));
                return _promise2["default"].reject('Initialize: No site id');
            }

            this._siteId = siteId;
            this._config = (0, _assign2["default"])(this._config, options);

            // Let's take a look at what's been queued up so far
            var trackCount = 0;
            var firstIdentifyIndex = -1;
            var identifyMethods = new _set2["default"]([METHODS.identify, METHODS.clear, METHODS.update]);
            this._queue.forEach(function (item, index) {
                if (item === null) return;

                var name = item[0];
                if (name === METHODS.track) {
                    var eventType = item[1];
                    if (EVENT_TYPES.view.has(eventType)) {
                        trackCount++;
                    }
                } else if (identifyMethods.has(name)) {
                    if (firstIdentifyIndex < 0) {
                        firstIdentifyIndex = index;
                    }
                }
            });

            // As we are prepending to the queue, the resulting calls will be:
            // 1. _identify()
            // 2. _loadOsrs() [if any]
            // 3. track('viewed') [if autoTrack is true]

            // First pop off the first identify command (if any)
            var identifyCommand = null;
            if (firstIdentifyIndex != -1) {
                identifyCommand = this._queue.splice(firstIdentifyIndex, 1)[0];
            }

            // Queue up auto track
            if (this._config.autoTrack) {
                if (trackCount === 0) {
                    this._queue.unshift([METHODS.track, DEFAULT_VIEW_EVENT, {
                        autoTrack: true,
                        'track_by_url': this._config.trackByUrl
                    }]);
                }
            }
            // Load OSRs
            this._queue.unshift(['_loadOsrs']);
            // Call _identify() first
            if (identifyCommand) {
                this._queue.unshift(identifyCommand);
            } else {
                this._queue.unshift([METHODS.identify]);
            }

            this._initialized = true;

            return this._processNextCommand()["finally"](function () {
                return _promise2["default"].resolve(onComplete());
            });
        }
    }, {
        key: 'version',
        value: function version() {
            return _config.VERSION;
        }
    }, {
        key: 'siteId',
        value: function siteId() {
            if (!this._siteId) {
                this._console.error(new Error('Library has not been initialized'));
                return null;
            }
            return this._siteId;
        }
    }, {
        key: 'currentId',
        value: function currentId() {
            return this._identity.currentId();
        }
    }, {
        key: 'track',
        value: function track(eventType) {
            var _this = this;

            var properties = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : {};
            var settings = arguments.length > 2 && arguments[2] !== undefined ? arguments[2] : {};

            var eventProps = null;
            switch (true) {
                case AUGMENT_AS_VIEW.has(eventType):
                    eventProps = this._trackView(properties);
                    break;
                case EVENT_TYPES.purchase.has(eventType):
                    eventProps = this._trackPurchase(properties);
                    break;
                case EVENT_TYPES.cart.has(eventType):
                    eventProps = this._trackUpdateCart(properties);
                    break;
                case EVENT_TYPES.signup.has(eventType):
                    eventProps = this._trackSignup(properties);
                    break;
                case EVENT_TYPES.search.has(eventType):
                    eventProps = _promise2["default"].resolve(properties);
                    break;
                default:
                    // Handle custom events
                    eventProps = _promise2["default"].resolve(properties);
                    break;
            }

            var onComplete = settings.onComplete || function () {};

            return eventProps.then(function (resolve) {
                var data = (0, _assign2["default"])({
                    type: eventType,
                    app: _this.siteId(),
                    bsin: _this._identity.bsin(),
                    'app_member_id': _this._identity.userId(),
                    // TODO: figure out if weird flip is correct
                    userId: _this.currentId(),
                    session: _this._session.id,
                    'doc_referrer': document.referrer
                }, resolve);

                if (!data.url) {
                    data.href = window.location.href;
                }

                var eventUrl = _this._config.apiEventHost + '/event/track';
                return (0, _io.sendRequest)(_this.siteId(), eventUrl, common.objectToMap(data), _this._config.useXhr, false);
            }).then(function (resolve) {
                var _resolve2 = (0, _slicedToArray3["default"])(resolve, 2),
                    response = _resolve2[0],
                    requestUrl = _resolve2[1];

                _this._pageResponses.push(response);
                _this._pageRequests.push(requestUrl);

                return _promise2["default"].resolve('Track: OK');
            }, function (reject) {
                return _promise2["default"].reject('Track: Error: ' + reject);
            })["finally"](function () {
                return _promise2["default"].resolve(onComplete());
            });
        }
    }, {
        key: 'updateUser',
        value: function updateUser() {
            var _this2 = this;

            var props = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};
            var settings = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : {};

            if (!props) return _promise2["default"].reject('UpdateUser: No properties');

            var onComplete = settings.onComplete || function () {};

            return this._identify().then(function (_resolve) {
                var peopleUrl = _this2._config.peopleHost + '/persons';
                var jsonData = common.JSONEncode({
                    $set: props,
                    bsin: _this2._identity.bsin()
                });
                var base64Data = common.base64Encode(jsonData);

                return (0, _io.sendRequest)(_this2.siteId(), peopleUrl, common.objectToMap({ data: base64Data }), _this2._config.useXhr);
            }, function (reject) {
                return _promise2["default"].reject('Identify: Error: ' + reject);
            }).then(function (resolve) {
                var _resolve3 = (0, _slicedToArray3["default"])(resolve, 2),
                    response = _resolve3[0],
                    requestUrl = _resolve3[1];

                _this2._pageResponses.push(response);
                _this2._pageRequests.push(requestUrl);

                _this2._identity.update(response);

                return _promise2["default"].resolve('UpdateUser: OK');
            }, function (reject) {
                return _promise2["default"].reject('UpdateUser: Error: ' + reject);
            })["finally"](function () {
                return _promise2["default"].resolve(onComplete());
            });
        }
    }, {
        key: 'clear',
        value: function clear() {
            var settings = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

            this._identity.remove();
            this._identity = new _identity.Identity();
            this._session.remove();
            this._session = new _session.Session();

            var onComplete = settings.onComplete || function () {};

            return this._identify({ _ignoreQuery: true, force: true })["finally"](function () {
                return _promise2["default"].resolve(onComplete());
            });
        }
    }, {
        key: 'push',
        value: function push() {
            if (!this._processing) {
                return this._processCommand(arguments.length <= 0 ? undefined : arguments[0]);
            } else {
                return _promise2["default"].resolve(this._queue.push(arguments.length <= 0 ? undefined : arguments[0]));
            }
        }
    }, {
        key: '_identify',
        value: function _identify() {
            var _this3 = this;

            var userIdentity = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

            var newSession = this._session.isNew();
            if (!userIdentity.force) {
                var currentBsin = this._identity.bsin();
                if (currentBsin && !newSession) {
                    this._console.log('Using prefetched identity');
                    return _promise2["default"].resolve('Identity: OK');
                }
            } else {
                this._console.log('Forcing identification');
            }
            var identity = this._identity.parseIdentity(userIdentity, true);

            var identityUrl = this._config.peopleHost + '/identify/resolve';
            var identityMap = common.objectToMap({ data: identity });

            return (0, _io.sendRequest)(this.siteId(), identityUrl, identityMap, this._config.useXhr).then(function (resolve) {
                var _resolve4 = (0, _slicedToArray3["default"])(resolve, 2),
                    response = _resolve4[0],
                    requestUrl = _resolve4[1];

                _this3._pageResponses.push(response);
                _this3._pageRequests.push(requestUrl);

                _this3._identity.update(response);

                return _promise2["default"].resolve('Identity: OK');
            }, function (reject) {
                _this3._console.error(new Error('Unable to identify user: ' + reject));
                return _promise2["default"].reject('Identity: Error: ' + reject);
            });
        }
    }, {
        key: '_trackView',
        value: function _trackView() {
            var _this4 = this;

            var props = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

            if ('resourceType' in props) {
                props.model = props['resourceType'];
                delete props['resourceType'];
            }

            return this._domReady()(function () {
                var bt = webpage.parseBT();
                var og = webpage.parseOGP();
                var twitter = webpage.parseTwitter();
                var schema = webpage.parseSchema();
                var meta = webpage.parseBasicMeta();
                var modDate = webpage.parseResourceProp('modDate', _this4._config.resourceSelectors) || bt.modDate || og['article:modified_time'] || schema.dateModified;
                var pageUrl = webpage.parseResourceProp('url', _this4._config.resourceSelectors) || bt.url || meta.url || og.url || twitter.url;
                var resourceType = (webpage.parseResourceProp('resource-type', _this4._config.resourceSelectors) || bt.type || og.type || 'item').replace(/^og:/, '').replace(/[^.A-Za-z0-9_-]/g, ''); // remove og: prefix and make slug-friendly

                if (pageUrl && !/^http/.test(pageUrl)) {
                    pageUrl = webpage.resolveRelativeUrl(pageUrl);
                }

                var eventProps = {
                    id: webpage.parseResourceProp('resource-id', _this4._config.resourceSelectors) || bt.id || (pageUrl ? (0, _md2["default"])(pageUrl) : null),
                    url: pageUrl,
                    model: resourceType
                };

                if (common.isValidDate(modDate)) {
                    eventProps.modDate = modDate;
                }

                return _promise2["default"].resolve((0, _assign2["default"])(eventProps, props));
            });
        }
    }, {
        key: '_trackSignup',
        value: function _trackSignup() {
            var _this5 = this;

            var props = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};


            var propertyMap = new _map2["default"]((0, _keys2["default"])(props).map(function (key) {
                return [key, props[key]];
            }));

            if (!(propertyMap.get('user_id') || propertyMap.get('email'))) {
                this._console.error('Require either user id or email address for signup tracking.');
                // TODO: figure out how to handle this error
                return {};
            }

            var personData = new _map2["default"]();
            var identifyData = new _map2["default"]();
            if (propertyMap.get('user_id')) {
                personData.set('user_id', propertyMap.get('user_id'));
                identifyData.set('user_id', propertyMap.get('user_id'));
                propertyMap["delete"]('user_id');
            }
            if (propertyMap.get('email')) {
                personData.set('email', propertyMap.get('email'));
                identifyData.set('email', propertyMap.get('email'));
                propertyMap["delete"]('email');
            }
            var dataFields = '';
            if (propertyMap.size) {
                dataFields = common.JSONEncode(common.mapToObject(propertyMap));
                personData.set('DATAFIELDS', dataFields);
            }

            return this._identify(common.mapToObject(identifyData)).then(function () {
                return _this5.updateUser(common.mapToObject(personData));
            }).then(function () {
                propertyMap["delete"]('user_id');
                propertyMap["delete"]('email');
                dataFields = '';
                if (propertyMap.size) {
                    dataFields = common.JSONEncode(common.mapToObject(propertyMap));
                }
                return { 'DATAFIELDS': dataFields };
            });
        }
    }, {
        key: '_getCartDetails',
        value: function _getCartDetails() {
            var props = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

            var shoppingCartItems = props.shoppingCartItems;
            if (!shoppingCartItems) {
                this._console.error('Empty shopping cart item list');
                return {};
            }
            if (!Array.isArray(shoppingCartItems)) {
                this._console.error('Shopping cart item list is not an array.  It should be.');
                shoppingCartItems = [shoppingCartItems];
            }

            // remove the shopping cart from the rest of the track props
            delete props.shoppingCartItems;

            var totalPurchaseAmount = shoppingCartItems.reduce(function (acc, item) {
                if (!(item.price && item.quantity)) return acc;
                return acc + parseFloat(item.price) * parseFloat(item.quantity);
            }, 0.0);

            // this is to support an older way of doing things where
            // shoppingCartItems and data were separate blobs
            if (props.data) {
                (0, _assign2["default"])(props, props.data);
                delete props.data;
            }

            return common.JSONEncode({
                'TOTAL': totalPurchaseAmount,
                'ITEMS': shoppingCartItems,
                'DATAFIELDS': props || {}
            });
        }
    }, {
        key: '_trackPurchase',
        value: function _trackPurchase() {
            var props = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

            return _promise2["default"].resolve({
                'LAST_PURCHASE': this._getCartDetails(props)
            });
        }
    }, {
        key: '_trackUpdateCart',
        value: function _trackUpdateCart() {
            var props = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};

            return _promise2["default"].resolve({
                'SHOPPING_CART': this._getCartDetails(props)
            });
        }

        // TODO: optimize this

    }, {
        key: '_loadOsrs',
        value: function _loadOsrs() {
            var _this6 = this;

            var activeSelectorsUrl = this._config.activeSelectors;

            var siteId = this.siteId();
            var pageParams = (0, _url.parseQueryString)();
            var isOnsiteTest = this._config.debug;

            if (!common.isString(siteId)) {
                this._console.error('siteId is not a string: ' + siteId);
                return _promise2["default"].reject('Bad site id: ' + siteId);
            }

            if (pageParams.has('bt_onsite_test')) {
                isOnsiteTest = pageParams.get('bt_onsite_test');
            }

            var data = common.objectToMap({
                'site_id': siteId,
                'bt_onsite_test': isOnsiteTest
            });

            return (0, _io.sendRequest)(siteId, activeSelectorsUrl, data, this._config.useXhr, false).then(function (resolve) {
                var _resolve5 = (0, _slicedToArray3["default"])(resolve, 2),
                    response = _resolve5[0],
                    requestUrl = _resolve5[1];

                _this6._pageResponses.push(response);
                _this6._pageRequests.push(requestUrl);

                var userId = _this6._identity.userId();
                var bsin = _this6._identity.bsin();

                _this6._domReady()(function () {
                    if (Array.isArray(response)) {
                        response.forEach(function (selector) {
                            var isElement = document.querySelector(String(selector));
                            if (isElement) {
                                var dataRec = common.objectToMap({
                                    'site_id': siteId,
                                    'user_id': userId,
                                    bsin: bsin,
                                    selectors: selector,
                                    'bt_onsite_test': isOnsiteTest
                                });

                                _this6._loadRecommendations(dataRec);
                            }
                        });
                    }
                });
            }, function (reject) {
                _this6._console.log('No onsite selectors: ' + reject);
            });
        }
    }, {
        key: '_loadRecommendations',
        value: function _loadRecommendations(data) {
            var _this7 = this;

            var recsUrl = this._config.onsiteHost;

            return (0, _io.sendRequest)(this.siteId(), recsUrl, data, this._config.useXhr).then(function (resolve) {
                var _resolve6 = (0, _slicedToArray3["default"])(resolve, 2),
                    response = _resolve6[0],
                    requestUrl = _resolve6[1];

                _this7._pageResponses.push(response);
                _this7._pageRequests.push(requestUrl);

                response = common.objectToMap(response);
                response.forEach(function (val, selector) {
                    var element = document.querySelector(String(selector));
                    var onsiteElement = document.createElement('div');
                    onsiteElement.innerHTML = val.html;
                    if (val.placement === 'append') {
                        element.appendChild(onsiteElement);
                    } else if (val.placement === 'prepend') {
                        if (element.childNodes.length > 0) {
                            element.insertBefore(onsiteElement, element.childNodes[0]);
                        } else {
                            element.appendChild(onsiteElement);
                        }
                    } else {
                        element.innerHTML = onsiteElement.innerHTML;
                    }
                });
            }, function (reject) {
                _this7._console.error('Unable to get onsite recommendations: ' + reject);
            });
        }
    }, {
        key: '_processNextCommand',
        value: function _processNextCommand() {
            if (this._queue.length) {
                var command = this._queue.shift();
                return this._processCommand(command);
            }
            return _promise2["default"].resolve('OK');
        }
    }, {
        key: '_processCommand',
        value: function _processCommand(command) {
            var self = this;
            self._processing = true;
            command = Array.prototype.slice.call(command);

            var asyncCommands = new _set2["default"](['_loadOsrs', 'track']);

            var fn = self[command[0]];
            if (typeof fn != 'function') {
                this._console.error(new Error(command[0] + ' is not a function.'));
                self._processing = false;
                return self._processNextCommand();
            }
            if (asyncCommands.has(command[0])) {
                return _promise2["default"].all([fn.apply(self, command.slice(1)), new _promise2["default"](function (resolve, _reject) {
                    self._processing = false;
                    resolve(self._processNextCommand());
                })]);
            }
            return fn.apply(self, command.slice(1))["finally"](function () {
                self._processing = false;
                return self._processNextCommand();
            });
        }
    }, {
        key: '_domReady',
        value: function _domReady() {
            var fns = [];
            var doc = document;
            var domContentLoaded = 'DOMContentLoaded';
            var hack = doc.documentElement.doScroll;
            var loaded = (hack ? /^loaded|^c/ : /^loaded|^i|^c/).test(doc.readyState);
            var isTest = this._config.test;

            if (!loaded) {
                var _listener = function listener() {
                    doc.removeEventListener(domContentLoaded, _listener);
                    loaded = 1;
                    while (_listener = fns.shift()) {
                        _listener();
                    }
                };
                doc.addEventListener(domContentLoaded, _listener);
            }
            return function (fn) {
                return _promise2["default"].resolve(loaded ? isTest ? fn() : setTimeout(fn, 0) : fns.push(fn));
            };
        }
    }, {
        key: '_setUpScrollTracking',
        value: function _setUpScrollTracking() {
            var _this8 = this;

            var self = this;

            var handleScroll = function handleScroll() {
                if (self._maxScrollablePixels == null) {
                    self._maxScrollablePixels = webpage.documentHeight() - webpage.browserHeight();
                }
                var percentScrolled = webpage.percentScrolled(self._maxScrollablePixels);

                var scrollPositions = self._config.scrollTrackLevels;
                scrollPositions.forEach(function (val) {
                    if (percentScrolled >= val) {
                        if (!self._scrollLevelsReached.has(val)) {
                            self._scrollLevelsReached.add(val);
                            self.push(['track', DEFAULT_SCROLL_EVENT, {
                                percent: val,
                                time: Math.floor((window.performance.now() - _this8._loadTime) / 1000)
                            }]);
                        }
                    }
                });
            };

            var handleResize = function handleResize() {
                _this8._maxScrollablePixels = null;
            };

            window.addEventListener('scroll', handleScroll, false);
            window.addEventListener('resize', handleResize, false);
        }
    }], [{
        key: 'create',
        value: function create() {
            var bt = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : [];

            var queue = bt;
            bt = window._bt = new BT(queue);

            // queue up query string method calls
            // TODO: can we restrict this to just the `bt_alias` calls?
            var notMethods = new _set2["default"](['bt_bsin', 'bt_app_member_id', 'bt_user_id', 'bt_email', 'bt_ee']);
            window.location.search.substring(1).split('&').forEach(function (query) {
                var _query$split = query.split('='),
                    _query$split2 = (0, _slicedToArray3["default"])(_query$split, 2),
                    key = _query$split2[0],
                    value = _query$split2[1];

                // skip non-BT parameters


                if (!/^bt_/.test(key)) return;
                // skip non-method parameters
                if (notMethods.has(key)) return;

                var method = key.replace('bt_', '');
                var args = [];
                try {
                    args = common.JSONDecode(common.base64Decode(decodeURIComponent(value)));
                } catch (error) {
                    bt._console.error(new Error('Could not parse ' + key + ' value.  It should be a base64-encoded JSON string.'));
                }

                if (Array.isArray(args)) {
                    bt._queue.push([method].concat(args));
                } else if (common.isObject(args) && (0, _is2["default"])(method, 'alias')) {
                    // TODO: figure out this `alias` rubbish
                    bt._queue.push([METHODS.identify, { 'new_bsin': args.userId, force: true }]);
                }
            });

            // is there an 'initialize' in the queue?
            // if there is, process it immediately
            var initIndex = -1;
            bt._queue.forEach(function (item, index) {
                if (item == null) return;

                var name = item[0];
                if (name == METHODS.init) {
                    initIndex = index;
                }
            });
            if (initIndex >= 0) {
                var initCommand = Array.prototype.slice.call(bt._queue.splice(initIndex, 1)[0]);
                var fn = bt[initCommand[0]];
                return fn.apply(bt, initCommand.slice(1));
            }
            return _promise2["default"].resolve('OK: Created.');
        }
    }]);
    return BT;
}();

/***/ }),
/* 89 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(90);
module.exports = __webpack_require__(0).Object.is;


/***/ }),
/* 90 */
/***/ (function(module, exports, __webpack_require__) {

// 19.1.3.10 Object.is(value1, value2)
var $export = __webpack_require__(1);
$export($export.S, 'Object', { is: __webpack_require__(91) });


/***/ }),
/* 91 */
/***/ (function(module, exports) {

// 7.2.9 SameValue(x, y)
module.exports = Object.is || function is(x, y) {
  // eslint-disable-next-line no-self-compare
  return x === y ? x !== 0 || 1 / x === 1 / y : x != x && y != y;
};


/***/ }),
/* 92 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(39);
__webpack_require__(11);
__webpack_require__(18);
__webpack_require__(100);
__webpack_require__(105);
__webpack_require__(107);
__webpack_require__(108);
module.exports = __webpack_require__(0).Map;


/***/ }),
/* 93 */
/***/ (function(module, exports, __webpack_require__) {

var toInteger = __webpack_require__(34);
var defined = __webpack_require__(32);
// true  -> String#at
// false -> String#codePointAt
module.exports = function (TO_STRING) {
  return function (that, pos) {
    var s = String(defined(that));
    var i = toInteger(pos);
    var l = s.length;
    var a, b;
    if (i < 0 || i >= l) return TO_STRING ? '' : undefined;
    a = s.charCodeAt(i);
    return a < 0xd800 || a > 0xdbff || i + 1 === l || (b = s.charCodeAt(i + 1)) < 0xdc00 || b > 0xdfff
      ? TO_STRING ? s.charAt(i) : a
      : TO_STRING ? s.slice(i, i + 2) : (a - 0xd800 << 10) + (b - 0xdc00) + 0x10000;
  };
};


/***/ }),
/* 94 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = __webpack_require__(9);


/***/ }),
/* 95 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var create = __webpack_require__(52);
var descriptor = __webpack_require__(38);
var setToStringTag = __webpack_require__(25);
var IteratorPrototype = {};

// 25.1.2.1.1 %IteratorPrototype%[@@iterator]()
__webpack_require__(9)(IteratorPrototype, __webpack_require__(2)('iterator'), function () { return this; });

module.exports = function (Constructor, NAME, next) {
  Constructor.prototype = create(IteratorPrototype, { next: descriptor(1, next) });
  setToStringTag(Constructor, NAME + ' Iterator');
};


/***/ }),
/* 96 */
/***/ (function(module, exports, __webpack_require__) {

var dP = __webpack_require__(5);
var anObject = __webpack_require__(7);
var getKeys = __webpack_require__(22);

module.exports = __webpack_require__(8) ? Object.defineProperties : function defineProperties(O, Properties) {
  anObject(O);
  var keys = getKeys(Properties);
  var length = keys.length;
  var i = 0;
  var P;
  while (length > i) dP.f(O, P = keys[i++], Properties[P]);
  return O;
};


/***/ }),
/* 97 */
/***/ (function(module, exports, __webpack_require__) {

// 19.1.2.9 / 15.2.3.2 Object.getPrototypeOf(O)
var has = __webpack_require__(14);
var toObject = __webpack_require__(13);
var IE_PROTO = __webpack_require__(35)('IE_PROTO');
var ObjectProto = Object.prototype;

module.exports = Object.getPrototypeOf || function (O) {
  O = toObject(O);
  if (has(O, IE_PROTO)) return O[IE_PROTO];
  if (typeof O.constructor == 'function' && O instanceof O.constructor) {
    return O.constructor.prototype;
  } return O instanceof Object ? ObjectProto : null;
};


/***/ }),
/* 98 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var addToUnscopables = __webpack_require__(99);
var step = __webpack_require__(54);
var Iterators = __webpack_require__(12);
var toIObject = __webpack_require__(23);

// 22.1.3.4 Array.prototype.entries()
// 22.1.3.13 Array.prototype.keys()
// 22.1.3.29 Array.prototype.values()
// 22.1.3.30 Array.prototype[@@iterator]()
module.exports = __webpack_require__(40)(Array, 'Array', function (iterated, kind) {
  this._t = toIObject(iterated); // target
  this._i = 0;                   // next index
  this._k = kind;                // kind
// 22.1.5.2.1 %ArrayIteratorPrototype%.next()
}, function () {
  var O = this._t;
  var kind = this._k;
  var index = this._i++;
  if (!O || index >= O.length) {
    this._t = undefined;
    return step(1);
  }
  if (kind == 'keys') return step(0, index);
  if (kind == 'values') return step(0, O[index]);
  return step(0, [index, O[index]]);
}, 'values');

// argumentsList[@@iterator] is %ArrayProto_values% (9.4.4.6, 9.4.4.7)
Iterators.Arguments = Iterators.Array;

addToUnscopables('keys');
addToUnscopables('values');
addToUnscopables('entries');


/***/ }),
/* 99 */
/***/ (function(module, exports) {

module.exports = function () { /* empty */ };


/***/ }),
/* 100 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var strong = __webpack_require__(55);
var validate = __webpack_require__(44);
var MAP = 'Map';

// 23.1 Map Objects
module.exports = __webpack_require__(60)(MAP, function (get) {
  return function Map() { return get(this, arguments.length > 0 ? arguments[0] : undefined); };
}, {
  // 23.1.3.6 Map.prototype.get(key)
  get: function get(key) {
    var entry = strong.getEntry(validate(this, MAP), key);
    return entry && entry.v;
  },
  // 23.1.3.9 Map.prototype.set(key, value)
  set: function set(key, value) {
    return strong.def(validate(this, MAP), key === 0 ? 0 : key, value);
  }
}, strong, true);


/***/ }),
/* 101 */
/***/ (function(module, exports, __webpack_require__) {

// 0 -> Array#forEach
// 1 -> Array#map
// 2 -> Array#filter
// 3 -> Array#some
// 4 -> Array#every
// 5 -> Array#find
// 6 -> Array#findIndex
var ctx = __webpack_require__(6);
var IObject = __webpack_require__(33);
var toObject = __webpack_require__(13);
var toLength = __webpack_require__(24);
var asc = __webpack_require__(102);
module.exports = function (TYPE, $create) {
  var IS_MAP = TYPE == 1;
  var IS_FILTER = TYPE == 2;
  var IS_SOME = TYPE == 3;
  var IS_EVERY = TYPE == 4;
  var IS_FIND_INDEX = TYPE == 6;
  var NO_HOLES = TYPE == 5 || IS_FIND_INDEX;
  var create = $create || asc;
  return function ($this, callbackfn, that) {
    var O = toObject($this);
    var self = IObject(O);
    var f = ctx(callbackfn, that, 3);
    var length = toLength(self.length);
    var index = 0;
    var result = IS_MAP ? create($this, length) : IS_FILTER ? create($this, 0) : undefined;
    var val, res;
    for (;length > index; index++) if (NO_HOLES || index in self) {
      val = self[index];
      res = f(val, index, O);
      if (TYPE) {
        if (IS_MAP) result[index] = res;   // map
        else if (res) switch (TYPE) {
          case 3: return true;             // some
          case 5: return val;              // find
          case 6: return index;            // findIndex
          case 2: result.push(val);        // filter
        } else if (IS_EVERY) return false; // every
      }
    }
    return IS_FIND_INDEX ? -1 : IS_SOME || IS_EVERY ? IS_EVERY : result;
  };
};


/***/ }),
/* 102 */
/***/ (function(module, exports, __webpack_require__) {

// 9.4.2.3 ArraySpeciesCreate(originalArray, length)
var speciesConstructor = __webpack_require__(103);

module.exports = function (original, length) {
  return new (speciesConstructor(original))(length);
};


/***/ }),
/* 103 */
/***/ (function(module, exports, __webpack_require__) {

var isObject = __webpack_require__(4);
var isArray = __webpack_require__(104);
var SPECIES = __webpack_require__(2)('species');

module.exports = function (original) {
  var C;
  if (isArray(original)) {
    C = original.constructor;
    // cross-realm fallback
    if (typeof C == 'function' && (C === Array || isArray(C.prototype))) C = undefined;
    if (isObject(C)) {
      C = C[SPECIES];
      if (C === null) C = undefined;
    }
  } return C === undefined ? Array : C;
};


/***/ }),
/* 104 */
/***/ (function(module, exports, __webpack_require__) {

// 7.2.2 IsArray(argument)
var cof = __webpack_require__(15);
module.exports = Array.isArray || function isArray(arg) {
  return cof(arg) == 'Array';
};


/***/ }),
/* 105 */
/***/ (function(module, exports, __webpack_require__) {

// https://github.com/DavidBruant/Map-Set.prototype.toJSON
var $export = __webpack_require__(1);

$export($export.P + $export.R, 'Map', { toJSON: __webpack_require__(61)('Map') });


/***/ }),
/* 106 */
/***/ (function(module, exports, __webpack_require__) {

var forOf = __webpack_require__(19);

module.exports = function (iter, ITERATOR) {
  var result = [];
  forOf(iter, false, result.push, result, ITERATOR);
  return result;
};


/***/ }),
/* 107 */
/***/ (function(module, exports, __webpack_require__) {

// https://tc39.github.io/proposal-setmap-offrom/#sec-map.of
__webpack_require__(62)('Map');


/***/ }),
/* 108 */
/***/ (function(module, exports, __webpack_require__) {

// https://tc39.github.io/proposal-setmap-offrom/#sec-map.from
__webpack_require__(63)('Map');


/***/ }),
/* 109 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(110), __esModule: true };

/***/ }),
/* 110 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(18);
__webpack_require__(11);
module.exports = __webpack_require__(111);


/***/ }),
/* 111 */
/***/ (function(module, exports, __webpack_require__) {

var classof = __webpack_require__(26);
var ITERATOR = __webpack_require__(2)('iterator');
var Iterators = __webpack_require__(12);
module.exports = __webpack_require__(0).isIterable = function (it) {
  var O = Object(it);
  return O[ITERATOR] !== undefined
    || '@@iterator' in O
    // eslint-disable-next-line no-prototype-builtins
    || Iterators.hasOwnProperty(classof(O));
};


/***/ }),
/* 112 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(18);
__webpack_require__(11);
module.exports = __webpack_require__(113);


/***/ }),
/* 113 */
/***/ (function(module, exports, __webpack_require__) {

var anObject = __webpack_require__(7);
var get = __webpack_require__(43);
module.exports = __webpack_require__(0).getIterator = function (it) {
  var iterFn = get(it);
  if (typeof iterFn != 'function') throw TypeError(it + ' is not iterable!');
  return anObject(iterFn.call(it));
};


/***/ }),
/* 114 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(39);
__webpack_require__(11);
__webpack_require__(18);
__webpack_require__(115);
__webpack_require__(118);
__webpack_require__(119);
module.exports = __webpack_require__(0).Promise;


/***/ }),
/* 115 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var LIBRARY = __webpack_require__(51);
var global = __webpack_require__(3);
var ctx = __webpack_require__(6);
var classof = __webpack_require__(26);
var $export = __webpack_require__(1);
var isObject = __webpack_require__(4);
var aFunction = __webpack_require__(16);
var anInstance = __webpack_require__(42);
var forOf = __webpack_require__(19);
var speciesConstructor = __webpack_require__(65);
var task = __webpack_require__(66).set;
var microtask = __webpack_require__(117)();
var newPromiseCapabilityModule = __webpack_require__(45);
var perform = __webpack_require__(67);
var promiseResolve = __webpack_require__(68);
var PROMISE = 'Promise';
var TypeError = global.TypeError;
var process = global.process;
var $Promise = global[PROMISE];
var isNode = classof(process) == 'process';
var empty = function () { /* empty */ };
var Internal, newGenericPromiseCapability, OwnPromiseCapability, Wrapper;
var newPromiseCapability = newGenericPromiseCapability = newPromiseCapabilityModule.f;

var USE_NATIVE = !!function () {
  try {
    // correct subclassing with @@species support
    var promise = $Promise.resolve(1);
    var FakePromise = (promise.constructor = {})[__webpack_require__(2)('species')] = function (exec) {
      exec(empty, empty);
    };
    // unhandled rejections tracking support, NodeJS Promise without it fails @@species test
    return (isNode || typeof PromiseRejectionEvent == 'function') && promise.then(empty) instanceof FakePromise;
  } catch (e) { /* empty */ }
}();

// helpers
var isThenable = function (it) {
  var then;
  return isObject(it) && typeof (then = it.then) == 'function' ? then : false;
};
var notify = function (promise, isReject) {
  if (promise._n) return;
  promise._n = true;
  var chain = promise._c;
  microtask(function () {
    var value = promise._v;
    var ok = promise._s == 1;
    var i = 0;
    var run = function (reaction) {
      var handler = ok ? reaction.ok : reaction.fail;
      var resolve = reaction.resolve;
      var reject = reaction.reject;
      var domain = reaction.domain;
      var result, then;
      try {
        if (handler) {
          if (!ok) {
            if (promise._h == 2) onHandleUnhandled(promise);
            promise._h = 1;
          }
          if (handler === true) result = value;
          else {
            if (domain) domain.enter();
            result = handler(value);
            if (domain) domain.exit();
          }
          if (result === reaction.promise) {
            reject(TypeError('Promise-chain cycle'));
          } else if (then = isThenable(result)) {
            then.call(result, resolve, reject);
          } else resolve(result);
        } else reject(value);
      } catch (e) {
        reject(e);
      }
    };
    while (chain.length > i) run(chain[i++]); // variable length - can't use forEach
    promise._c = [];
    promise._n = false;
    if (isReject && !promise._h) onUnhandled(promise);
  });
};
var onUnhandled = function (promise) {
  task.call(global, function () {
    var value = promise._v;
    var unhandled = isUnhandled(promise);
    var result, handler, console;
    if (unhandled) {
      result = perform(function () {
        if (isNode) {
          process.emit('unhandledRejection', value, promise);
        } else if (handler = global.onunhandledrejection) {
          handler({ promise: promise, reason: value });
        } else if ((console = global.console) && console.error) {
          console.error('Unhandled promise rejection', value);
        }
      });
      // Browsers should not trigger `rejectionHandled` event if it was handled here, NodeJS - should
      promise._h = isNode || isUnhandled(promise) ? 2 : 1;
    } promise._a = undefined;
    if (unhandled && result.e) throw result.v;
  });
};
var isUnhandled = function (promise) {
  if (promise._h == 1) return false;
  var chain = promise._a || promise._c;
  var i = 0;
  var reaction;
  while (chain.length > i) {
    reaction = chain[i++];
    if (reaction.fail || !isUnhandled(reaction.promise)) return false;
  } return true;
};
var onHandleUnhandled = function (promise) {
  task.call(global, function () {
    var handler;
    if (isNode) {
      process.emit('rejectionHandled', promise);
    } else if (handler = global.onrejectionhandled) {
      handler({ promise: promise, reason: promise._v });
    }
  });
};
var $reject = function (value) {
  var promise = this;
  if (promise._d) return;
  promise._d = true;
  promise = promise._w || promise; // unwrap
  promise._v = value;
  promise._s = 2;
  if (!promise._a) promise._a = promise._c.slice();
  notify(promise, true);
};
var $resolve = function (value) {
  var promise = this;
  var then;
  if (promise._d) return;
  promise._d = true;
  promise = promise._w || promise; // unwrap
  try {
    if (promise === value) throw TypeError("Promise can't be resolved itself");
    if (then = isThenable(value)) {
      microtask(function () {
        var wrapper = { _w: promise, _d: false }; // wrap
        try {
          then.call(value, ctx($resolve, wrapper, 1), ctx($reject, wrapper, 1));
        } catch (e) {
          $reject.call(wrapper, e);
        }
      });
    } else {
      promise._v = value;
      promise._s = 1;
      notify(promise, false);
    }
  } catch (e) {
    $reject.call({ _w: promise, _d: false }, e); // wrap
  }
};

// constructor polyfill
if (!USE_NATIVE) {
  // 25.4.3.1 Promise(executor)
  $Promise = function Promise(executor) {
    anInstance(this, $Promise, PROMISE, '_h');
    aFunction(executor);
    Internal.call(this);
    try {
      executor(ctx($resolve, this, 1), ctx($reject, this, 1));
    } catch (err) {
      $reject.call(this, err);
    }
  };
  // eslint-disable-next-line no-unused-vars
  Internal = function Promise(executor) {
    this._c = [];             // <- awaiting reactions
    this._a = undefined;      // <- checked in isUnhandled reactions
    this._s = 0;              // <- state
    this._d = false;          // <- done
    this._v = undefined;      // <- value
    this._h = 0;              // <- rejection state, 0 - default, 1 - handled, 2 - unhandled
    this._n = false;          // <- notify
  };
  Internal.prototype = __webpack_require__(41)($Promise.prototype, {
    // 25.4.5.3 Promise.prototype.then(onFulfilled, onRejected)
    then: function then(onFulfilled, onRejected) {
      var reaction = newPromiseCapability(speciesConstructor(this, $Promise));
      reaction.ok = typeof onFulfilled == 'function' ? onFulfilled : true;
      reaction.fail = typeof onRejected == 'function' && onRejected;
      reaction.domain = isNode ? process.domain : undefined;
      this._c.push(reaction);
      if (this._a) this._a.push(reaction);
      if (this._s) notify(this, false);
      return reaction.promise;
    },
    // 25.4.5.1 Promise.prototype.catch(onRejected)
    'catch': function (onRejected) {
      return this.then(undefined, onRejected);
    }
  });
  OwnPromiseCapability = function () {
    var promise = new Internal();
    this.promise = promise;
    this.resolve = ctx($resolve, promise, 1);
    this.reject = ctx($reject, promise, 1);
  };
  newPromiseCapabilityModule.f = newPromiseCapability = function (C) {
    return C === $Promise || C === Wrapper
      ? new OwnPromiseCapability(C)
      : newGenericPromiseCapability(C);
  };
}

$export($export.G + $export.W + $export.F * !USE_NATIVE, { Promise: $Promise });
__webpack_require__(25)($Promise, PROMISE);
__webpack_require__(58)(PROMISE);
Wrapper = __webpack_require__(0)[PROMISE];

// statics
$export($export.S + $export.F * !USE_NATIVE, PROMISE, {
  // 25.4.4.5 Promise.reject(r)
  reject: function reject(r) {
    var capability = newPromiseCapability(this);
    var $$reject = capability.reject;
    $$reject(r);
    return capability.promise;
  }
});
$export($export.S + $export.F * (LIBRARY || !USE_NATIVE), PROMISE, {
  // 25.4.4.6 Promise.resolve(x)
  resolve: function resolve(x) {
    return promiseResolve(LIBRARY && this === Wrapper ? $Promise : this, x);
  }
});
$export($export.S + $export.F * !(USE_NATIVE && __webpack_require__(69)(function (iter) {
  $Promise.all(iter)['catch'](empty);
})), PROMISE, {
  // 25.4.4.1 Promise.all(iterable)
  all: function all(iterable) {
    var C = this;
    var capability = newPromiseCapability(C);
    var resolve = capability.resolve;
    var reject = capability.reject;
    var result = perform(function () {
      var values = [];
      var index = 0;
      var remaining = 1;
      forOf(iterable, false, function (promise) {
        var $index = index++;
        var alreadyCalled = false;
        values.push(undefined);
        remaining++;
        C.resolve(promise).then(function (value) {
          if (alreadyCalled) return;
          alreadyCalled = true;
          values[$index] = value;
          --remaining || resolve(values);
        }, reject);
      });
      --remaining || resolve(values);
    });
    if (result.e) reject(result.v);
    return capability.promise;
  },
  // 25.4.4.4 Promise.race(iterable)
  race: function race(iterable) {
    var C = this;
    var capability = newPromiseCapability(C);
    var reject = capability.reject;
    var result = perform(function () {
      forOf(iterable, false, function (promise) {
        C.resolve(promise).then(capability.resolve, reject);
      });
    });
    if (result.e) reject(result.v);
    return capability.promise;
  }
});


/***/ }),
/* 116 */
/***/ (function(module, exports) {

// fast apply, http://jsperf.lnkit.com/fast-apply/5
module.exports = function (fn, args, that) {
  var un = that === undefined;
  switch (args.length) {
    case 0: return un ? fn()
                      : fn.call(that);
    case 1: return un ? fn(args[0])
                      : fn.call(that, args[0]);
    case 2: return un ? fn(args[0], args[1])
                      : fn.call(that, args[0], args[1]);
    case 3: return un ? fn(args[0], args[1], args[2])
                      : fn.call(that, args[0], args[1], args[2]);
    case 4: return un ? fn(args[0], args[1], args[2], args[3])
                      : fn.call(that, args[0], args[1], args[2], args[3]);
  } return fn.apply(that, args);
};


/***/ }),
/* 117 */
/***/ (function(module, exports, __webpack_require__) {

var global = __webpack_require__(3);
var macrotask = __webpack_require__(66).set;
var Observer = global.MutationObserver || global.WebKitMutationObserver;
var process = global.process;
var Promise = global.Promise;
var isNode = __webpack_require__(15)(process) == 'process';

module.exports = function () {
  var head, last, notify;

  var flush = function () {
    var parent, fn;
    if (isNode && (parent = process.domain)) parent.exit();
    while (head) {
      fn = head.fn;
      head = head.next;
      try {
        fn();
      } catch (e) {
        if (head) notify();
        else last = undefined;
        throw e;
      }
    } last = undefined;
    if (parent) parent.enter();
  };

  // Node.js
  if (isNode) {
    notify = function () {
      process.nextTick(flush);
    };
  // browsers with MutationObserver
  } else if (Observer) {
    var toggle = true;
    var node = document.createTextNode('');
    new Observer(flush).observe(node, { characterData: true }); // eslint-disable-line no-new
    notify = function () {
      node.data = toggle = !toggle;
    };
  // environments with maybe non-completely correct, but existent Promise
  } else if (Promise && Promise.resolve) {
    var promise = Promise.resolve();
    notify = function () {
      promise.then(flush);
    };
  // for other environments - macrotask based on:
  // - setImmediate
  // - MessageChannel
  // - window.postMessag
  // - onreadystatechange
  // - setTimeout
  } else {
    notify = function () {
      // strange IE + webpack dev server bug - use .call(global)
      macrotask.call(global, flush);
    };
  }

  return function (fn) {
    var task = { fn: fn, next: undefined };
    if (last) last.next = task;
    if (!head) {
      head = task;
      notify();
    } last = task;
  };
};


/***/ }),
/* 118 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";
// https://github.com/tc39/proposal-promise-finally

var $export = __webpack_require__(1);
var core = __webpack_require__(0);
var global = __webpack_require__(3);
var speciesConstructor = __webpack_require__(65);
var promiseResolve = __webpack_require__(68);

$export($export.P + $export.R, 'Promise', { 'finally': function (onFinally) {
  var C = speciesConstructor(this, core.Promise || global.Promise);
  var isFunction = typeof onFinally == 'function';
  return this.then(
    isFunction ? function (x) {
      return promiseResolve(C, onFinally()).then(function () { return x; });
    } : onFinally,
    isFunction ? function (e) {
      return promiseResolve(C, onFinally()).then(function () { throw e; });
    } : onFinally
  );
} });


/***/ }),
/* 119 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

// https://github.com/tc39/proposal-promise-try
var $export = __webpack_require__(1);
var newPromiseCapability = __webpack_require__(45);
var perform = __webpack_require__(67);

$export($export.S, 'Promise', { 'try': function (callbackfn) {
  var promiseCapability = newPromiseCapability.f(this);
  var result = perform(callbackfn);
  (result.e ? promiseCapability.reject : promiseCapability.resolve)(result.v);
  return promiseCapability.promise;
} });


/***/ }),
/* 120 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(121);
module.exports = __webpack_require__(0).Object.assign;


/***/ }),
/* 121 */
/***/ (function(module, exports, __webpack_require__) {

// 19.1.3.1 Object.assign(target, source)
var $export = __webpack_require__(1);

$export($export.S + $export.F, 'Object', { assign: __webpack_require__(122) });


/***/ }),
/* 122 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

// 19.1.2.1 Object.assign(target, source, ...)
var getKeys = __webpack_require__(22);
var gOPS = __webpack_require__(123);
var pIE = __webpack_require__(49);
var toObject = __webpack_require__(13);
var IObject = __webpack_require__(33);
var $assign = Object.assign;

// should work with symbols and should have deterministic property order (V8 bug)
module.exports = !$assign || __webpack_require__(10)(function () {
  var A = {};
  var B = {};
  // eslint-disable-next-line no-undef
  var S = Symbol();
  var K = 'abcdefghijklmnopqrst';
  A[S] = 7;
  K.split('').forEach(function (k) { B[k] = k; });
  return $assign({}, A)[S] != 7 || Object.keys($assign({}, B)).join('') != K;
}) ? function assign(target, source) { // eslint-disable-line no-unused-vars
  var T = toObject(target);
  var aLen = arguments.length;
  var index = 1;
  var getSymbols = gOPS.f;
  var isEnum = pIE.f;
  while (aLen > index) {
    var S = IObject(arguments[index++]);
    var keys = getSymbols ? getKeys(S).concat(getSymbols(S)) : getKeys(S);
    var length = keys.length;
    var j = 0;
    var key;
    while (length > j) if (isEnum.call(S, key = keys[j++])) T[key] = S[key];
  } return T;
} : $assign;


/***/ }),
/* 123 */
/***/ (function(module, exports) {

exports.f = Object.getOwnPropertySymbols;


/***/ }),
/* 124 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(125), __esModule: true };

/***/ }),
/* 125 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(126);
var $Object = __webpack_require__(0).Object;
module.exports = function defineProperty(it, key, desc) {
  return $Object.defineProperty(it, key, desc);
};


/***/ }),
/* 126 */
/***/ (function(module, exports, __webpack_require__) {

var $export = __webpack_require__(1);
// 19.1.2.4 / 15.2.3.6 Object.defineProperty(O, P, Attributes)
$export($export.S + $export.F * !__webpack_require__(8), 'Object', { defineProperty: __webpack_require__(5).f });


/***/ }),
/* 127 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


exports.__esModule = true;

var _from = __webpack_require__(70);

var _from2 = _interopRequireDefault(_from);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

exports["default"] = function (arr) {
  if (Array.isArray(arr)) {
    for (var i = 0, arr2 = Array(arr.length); i < arr.length; i++) {
      arr2[i] = arr[i];
    }

    return arr2;
  } else {
    return (0, _from2["default"])(arr);
  }
};

/***/ }),
/* 128 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(11);
__webpack_require__(129);
module.exports = __webpack_require__(0).Array.from;


/***/ }),
/* 129 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var ctx = __webpack_require__(6);
var $export = __webpack_require__(1);
var toObject = __webpack_require__(13);
var call = __webpack_require__(56);
var isArrayIter = __webpack_require__(57);
var toLength = __webpack_require__(24);
var createProperty = __webpack_require__(130);
var getIterFn = __webpack_require__(43);

$export($export.S + $export.F * !__webpack_require__(69)(function (iter) { Array.from(iter); }), 'Array', {
  // 22.1.2.1 Array.from(arrayLike, mapfn = undefined, thisArg = undefined)
  from: function from(arrayLike /* , mapfn = undefined, thisArg = undefined */) {
    var O = toObject(arrayLike);
    var C = typeof this == 'function' ? this : Array;
    var aLen = arguments.length;
    var mapfn = aLen > 1 ? arguments[1] : undefined;
    var mapping = mapfn !== undefined;
    var index = 0;
    var iterFn = getIterFn(O);
    var length, result, step, iterator;
    if (mapping) mapfn = ctx(mapfn, aLen > 2 ? arguments[2] : undefined, 2);
    // if object isn't iterable or it's array with default iterator - use simple case
    if (iterFn != undefined && !(C == Array && isArrayIter(iterFn))) {
      for (iterator = iterFn.call(O), result = new C(); !(step = iterator.next()).done; index++) {
        createProperty(result, index, mapping ? call(iterator, mapfn, [step.value, index], true) : step.value);
      }
    } else {
      length = toLength(O.length);
      for (result = new C(length); length > index; index++) {
        createProperty(result, index, mapping ? mapfn(O[index], index) : O[index]);
      }
    }
    result.length = index;
    return result;
  }
});


/***/ }),
/* 130 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var $defineProperty = __webpack_require__(5);
var createDesc = __webpack_require__(38);

module.exports = function (object, index, value) {
  if (index in object) $defineProperty.f(object, index, createDesc(0, value));
  else object[index] = value;
};


/***/ }),
/* 131 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(39);
__webpack_require__(11);
__webpack_require__(18);
__webpack_require__(132);
__webpack_require__(133);
__webpack_require__(134);
__webpack_require__(135);
module.exports = __webpack_require__(0).Set;


/***/ }),
/* 132 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";

var strong = __webpack_require__(55);
var validate = __webpack_require__(44);
var SET = 'Set';

// 23.2 Set Objects
module.exports = __webpack_require__(60)(SET, function (get) {
  return function Set() { return get(this, arguments.length > 0 ? arguments[0] : undefined); };
}, {
  // 23.2.3.1 Set.prototype.add(value)
  add: function add(value) {
    return strong.def(validate(this, SET), value = value === 0 ? 0 : value, value);
  }
}, strong);


/***/ }),
/* 133 */
/***/ (function(module, exports, __webpack_require__) {

// https://github.com/DavidBruant/Map-Set.prototype.toJSON
var $export = __webpack_require__(1);

$export($export.P + $export.R, 'Set', { toJSON: __webpack_require__(61)('Set') });


/***/ }),
/* 134 */
/***/ (function(module, exports, __webpack_require__) {

// https://tc39.github.io/proposal-setmap-offrom/#sec-set.of
__webpack_require__(62)('Set');


/***/ }),
/* 135 */
/***/ (function(module, exports, __webpack_require__) {

// https://tc39.github.io/proposal-setmap-offrom/#sec-set.from
__webpack_require__(63)('Set');


/***/ }),
/* 136 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(137), __esModule: true };

/***/ }),
/* 137 */
/***/ (function(module, exports, __webpack_require__) {

var core = __webpack_require__(0);
var $JSON = core.JSON || (core.JSON = { stringify: JSON.stringify });
module.exports = function stringify(it) { // eslint-disable-line no-unused-vars
  return $JSON.stringify.apply($JSON, arguments);
};


/***/ }),
/* 138 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = __webpack_require__(139);


/***/ }),
/* 139 */
/***/ (function(module, exports, __webpack_require__) {

// This method of obtaining a reference to the global object needs to be
// kept identical to the way it is obtained in runtime.js
var g = (function() { return this })() || Function("return this")();

// Use `getOwnPropertyNames` because not all browsers support calling
// `hasOwnProperty` on the global `self` object in a worker. See #183.
var hadRuntime = g.regeneratorRuntime &&
  Object.getOwnPropertyNames(g).indexOf("regeneratorRuntime") >= 0;

// Save the old regeneratorRuntime in case it needs to be restored later.
var oldRuntime = hadRuntime && g.regeneratorRuntime;

// Force reevalutation of runtime.js.
g.regeneratorRuntime = undefined;

module.exports = __webpack_require__(140);

if (hadRuntime) {
  // Restore the original runtime.
  g.regeneratorRuntime = oldRuntime;
} else {
  // Remove the global property added by runtime.js.
  try {
    delete g.regeneratorRuntime;
  } catch(e) {
    g.regeneratorRuntime = undefined;
  }
}


/***/ }),
/* 140 */
/***/ (function(module, exports) {

/**
 * Copyright (c) 2014, Facebook, Inc.
 * All rights reserved.
 *
 * This source code is licensed under the BSD-style license found in the
 * https://raw.github.com/facebook/regenerator/master/LICENSE file. An
 * additional grant of patent rights can be found in the PATENTS file in
 * the same directory.
 */

!(function(global) {
  "use strict";

  var Op = Object.prototype;
  var hasOwn = Op.hasOwnProperty;
  var undefined; // More compressible than void 0.
  var $Symbol = typeof Symbol === "function" ? Symbol : {};
  var iteratorSymbol = $Symbol.iterator || "@@iterator";
  var asyncIteratorSymbol = $Symbol.asyncIterator || "@@asyncIterator";
  var toStringTagSymbol = $Symbol.toStringTag || "@@toStringTag";

  var inModule = typeof module === "object";
  var runtime = global.regeneratorRuntime;
  if (runtime) {
    if (inModule) {
      // If regeneratorRuntime is defined globally and we're in a module,
      // make the exports object identical to regeneratorRuntime.
      module.exports = runtime;
    }
    // Don't bother evaluating the rest of this file if the runtime was
    // already defined globally.
    return;
  }

  // Define the runtime globally (as expected by generated code) as either
  // module.exports (if we're in a module) or a new, empty object.
  runtime = global.regeneratorRuntime = inModule ? module.exports : {};

  function wrap(innerFn, outerFn, self, tryLocsList) {
    // If outerFn provided and outerFn.prototype is a Generator, then outerFn.prototype instanceof Generator.
    var protoGenerator = outerFn && outerFn.prototype instanceof Generator ? outerFn : Generator;
    var generator = Object.create(protoGenerator.prototype);
    var context = new Context(tryLocsList || []);

    // The ._invoke method unifies the implementations of the .next,
    // .throw, and .return methods.
    generator._invoke = makeInvokeMethod(innerFn, self, context);

    return generator;
  }
  runtime.wrap = wrap;

  // Try/catch helper to minimize deoptimizations. Returns a completion
  // record like context.tryEntries[i].completion. This interface could
  // have been (and was previously) designed to take a closure to be
  // invoked without arguments, but in all the cases we care about we
  // already have an existing method we want to call, so there's no need
  // to create a new function object. We can even get away with assuming
  // the method takes exactly one argument, since that happens to be true
  // in every case, so we don't have to touch the arguments object. The
  // only additional allocation required is the completion record, which
  // has a stable shape and so hopefully should be cheap to allocate.
  function tryCatch(fn, obj, arg) {
    try {
      return { type: "normal", arg: fn.call(obj, arg) };
    } catch (err) {
      return { type: "throw", arg: err };
    }
  }

  var GenStateSuspendedStart = "suspendedStart";
  var GenStateSuspendedYield = "suspendedYield";
  var GenStateExecuting = "executing";
  var GenStateCompleted = "completed";

  // Returning this object from the innerFn has the same effect as
  // breaking out of the dispatch switch statement.
  var ContinueSentinel = {};

  // Dummy constructor functions that we use as the .constructor and
  // .constructor.prototype properties for functions that return Generator
  // objects. For full spec compliance, you may wish to configure your
  // minifier not to mangle the names of these two functions.
  function Generator() {}
  function GeneratorFunction() {}
  function GeneratorFunctionPrototype() {}

  // This is a polyfill for %IteratorPrototype% for environments that
  // don't natively support it.
  var IteratorPrototype = {};
  IteratorPrototype[iteratorSymbol] = function () {
    return this;
  };

  var getProto = Object.getPrototypeOf;
  var NativeIteratorPrototype = getProto && getProto(getProto(values([])));
  if (NativeIteratorPrototype &&
      NativeIteratorPrototype !== Op &&
      hasOwn.call(NativeIteratorPrototype, iteratorSymbol)) {
    // This environment has a native %IteratorPrototype%; use it instead
    // of the polyfill.
    IteratorPrototype = NativeIteratorPrototype;
  }

  var Gp = GeneratorFunctionPrototype.prototype =
    Generator.prototype = Object.create(IteratorPrototype);
  GeneratorFunction.prototype = Gp.constructor = GeneratorFunctionPrototype;
  GeneratorFunctionPrototype.constructor = GeneratorFunction;
  GeneratorFunctionPrototype[toStringTagSymbol] =
    GeneratorFunction.displayName = "GeneratorFunction";

  // Helper for defining the .next, .throw, and .return methods of the
  // Iterator interface in terms of a single ._invoke method.
  function defineIteratorMethods(prototype) {
    ["next", "throw", "return"].forEach(function(method) {
      prototype[method] = function(arg) {
        return this._invoke(method, arg);
      };
    });
  }

  runtime.isGeneratorFunction = function(genFun) {
    var ctor = typeof genFun === "function" && genFun.constructor;
    return ctor
      ? ctor === GeneratorFunction ||
        // For the native GeneratorFunction constructor, the best we can
        // do is to check its .name property.
        (ctor.displayName || ctor.name) === "GeneratorFunction"
      : false;
  };

  runtime.mark = function(genFun) {
    if (Object.setPrototypeOf) {
      Object.setPrototypeOf(genFun, GeneratorFunctionPrototype);
    } else {
      genFun.__proto__ = GeneratorFunctionPrototype;
      if (!(toStringTagSymbol in genFun)) {
        genFun[toStringTagSymbol] = "GeneratorFunction";
      }
    }
    genFun.prototype = Object.create(Gp);
    return genFun;
  };

  // Within the body of any async function, `await x` is transformed to
  // `yield regeneratorRuntime.awrap(x)`, so that the runtime can test
  // `hasOwn.call(value, "__await")` to determine if the yielded value is
  // meant to be awaited.
  runtime.awrap = function(arg) {
    return { __await: arg };
  };

  function AsyncIterator(generator) {
    function invoke(method, arg, resolve, reject) {
      var record = tryCatch(generator[method], generator, arg);
      if (record.type === "throw") {
        reject(record.arg);
      } else {
        var result = record.arg;
        var value = result.value;
        if (value &&
            typeof value === "object" &&
            hasOwn.call(value, "__await")) {
          return Promise.resolve(value.__await).then(function(value) {
            invoke("next", value, resolve, reject);
          }, function(err) {
            invoke("throw", err, resolve, reject);
          });
        }

        return Promise.resolve(value).then(function(unwrapped) {
          // When a yielded Promise is resolved, its final value becomes
          // the .value of the Promise<{value,done}> result for the
          // current iteration. If the Promise is rejected, however, the
          // result for this iteration will be rejected with the same
          // reason. Note that rejections of yielded Promises are not
          // thrown back into the generator function, as is the case
          // when an awaited Promise is rejected. This difference in
          // behavior between yield and await is important, because it
          // allows the consumer to decide what to do with the yielded
          // rejection (swallow it and continue, manually .throw it back
          // into the generator, abandon iteration, whatever). With
          // await, by contrast, there is no opportunity to examine the
          // rejection reason outside the generator function, so the
          // only option is to throw it from the await expression, and
          // let the generator function handle the exception.
          result.value = unwrapped;
          resolve(result);
        }, reject);
      }
    }

    var previousPromise;

    function enqueue(method, arg) {
      function callInvokeWithMethodAndArg() {
        return new Promise(function(resolve, reject) {
          invoke(method, arg, resolve, reject);
        });
      }

      return previousPromise =
        // If enqueue has been called before, then we want to wait until
        // all previous Promises have been resolved before calling invoke,
        // so that results are always delivered in the correct order. If
        // enqueue has not been called before, then it is important to
        // call invoke immediately, without waiting on a callback to fire,
        // so that the async generator function has the opportunity to do
        // any necessary setup in a predictable way. This predictability
        // is why the Promise constructor synchronously invokes its
        // executor callback, and why async functions synchronously
        // execute code before the first await. Since we implement simple
        // async functions in terms of async generators, it is especially
        // important to get this right, even though it requires care.
        previousPromise ? previousPromise.then(
          callInvokeWithMethodAndArg,
          // Avoid propagating failures to Promises returned by later
          // invocations of the iterator.
          callInvokeWithMethodAndArg
        ) : callInvokeWithMethodAndArg();
    }

    // Define the unified helper method that is used to implement .next,
    // .throw, and .return (see defineIteratorMethods).
    this._invoke = enqueue;
  }

  defineIteratorMethods(AsyncIterator.prototype);
  AsyncIterator.prototype[asyncIteratorSymbol] = function () {
    return this;
  };
  runtime.AsyncIterator = AsyncIterator;

  // Note that simple async functions are implemented on top of
  // AsyncIterator objects; they just return a Promise for the value of
  // the final result produced by the iterator.
  runtime.async = function(innerFn, outerFn, self, tryLocsList) {
    var iter = new AsyncIterator(
      wrap(innerFn, outerFn, self, tryLocsList)
    );

    return runtime.isGeneratorFunction(outerFn)
      ? iter // If outerFn is a generator, return the full iterator.
      : iter.next().then(function(result) {
          return result.done ? result.value : iter.next();
        });
  };

  function makeInvokeMethod(innerFn, self, context) {
    var state = GenStateSuspendedStart;

    return function invoke(method, arg) {
      if (state === GenStateExecuting) {
        throw new Error("Generator is already running");
      }

      if (state === GenStateCompleted) {
        if (method === "throw") {
          throw arg;
        }

        // Be forgiving, per 25.3.3.3.3 of the spec:
        // https://people.mozilla.org/~jorendorff/es6-draft.html#sec-generatorresume
        return doneResult();
      }

      context.method = method;
      context.arg = arg;

      while (true) {
        var delegate = context.delegate;
        if (delegate) {
          var delegateResult = maybeInvokeDelegate(delegate, context);
          if (delegateResult) {
            if (delegateResult === ContinueSentinel) continue;
            return delegateResult;
          }
        }

        if (context.method === "next") {
          // Setting context._sent for legacy support of Babel's
          // function.sent implementation.
          context.sent = context._sent = context.arg;

        } else if (context.method === "throw") {
          if (state === GenStateSuspendedStart) {
            state = GenStateCompleted;
            throw context.arg;
          }

          context.dispatchException(context.arg);

        } else if (context.method === "return") {
          context.abrupt("return", context.arg);
        }

        state = GenStateExecuting;

        var record = tryCatch(innerFn, self, context);
        if (record.type === "normal") {
          // If an exception is thrown from innerFn, we leave state ===
          // GenStateExecuting and loop back for another invocation.
          state = context.done
            ? GenStateCompleted
            : GenStateSuspendedYield;

          if (record.arg === ContinueSentinel) {
            continue;
          }

          return {
            value: record.arg,
            done: context.done
          };

        } else if (record.type === "throw") {
          state = GenStateCompleted;
          // Dispatch the exception by looping back around to the
          // context.dispatchException(context.arg) call above.
          context.method = "throw";
          context.arg = record.arg;
        }
      }
    };
  }

  // Call delegate.iterator[context.method](context.arg) and handle the
  // result, either by returning a { value, done } result from the
  // delegate iterator, or by modifying context.method and context.arg,
  // setting context.delegate to null, and returning the ContinueSentinel.
  function maybeInvokeDelegate(delegate, context) {
    var method = delegate.iterator[context.method];
    if (method === undefined) {
      // A .throw or .return when the delegate iterator has no .throw
      // method always terminates the yield* loop.
      context.delegate = null;

      if (context.method === "throw") {
        if (delegate.iterator["return"]) {
          // If the delegate iterator has a return method, give it a
          // chance to clean up.
          context.method = "return";
          context.arg = undefined;
          maybeInvokeDelegate(delegate, context);

          if (context.method === "throw") {
            // If maybeInvokeDelegate(context) changed context.method from
            // "return" to "throw", let that override the TypeError below.
            return ContinueSentinel;
          }
        }

        context.method = "throw";
        context.arg = new TypeError(
          "The iterator does not provide a 'throw' method");
      }

      return ContinueSentinel;
    }

    var record = tryCatch(method, delegate.iterator, context.arg);

    if (record.type === "throw") {
      context.method = "throw";
      context.arg = record.arg;
      context.delegate = null;
      return ContinueSentinel;
    }

    var info = record.arg;

    if (! info) {
      context.method = "throw";
      context.arg = new TypeError("iterator result is not an object");
      context.delegate = null;
      return ContinueSentinel;
    }

    if (info.done) {
      // Assign the result of the finished delegate to the temporary
      // variable specified by delegate.resultName (see delegateYield).
      context[delegate.resultName] = info.value;

      // Resume execution at the desired location (see delegateYield).
      context.next = delegate.nextLoc;

      // If context.method was "throw" but the delegate handled the
      // exception, let the outer generator proceed normally. If
      // context.method was "next", forget context.arg since it has been
      // "consumed" by the delegate iterator. If context.method was
      // "return", allow the original .return call to continue in the
      // outer generator.
      if (context.method !== "return") {
        context.method = "next";
        context.arg = undefined;
      }

    } else {
      // Re-yield the result returned by the delegate method.
      return info;
    }

    // The delegate iterator is finished, so forget it and continue with
    // the outer generator.
    context.delegate = null;
    return ContinueSentinel;
  }

  // Define Generator.prototype.{next,throw,return} in terms of the
  // unified ._invoke helper method.
  defineIteratorMethods(Gp);

  Gp[toStringTagSymbol] = "Generator";

  // A Generator should always return itself as the iterator object when the
  // @@iterator function is called on it. Some browsers' implementations of the
  // iterator prototype chain incorrectly implement this, causing the Generator
  // object to not be returned from this call. This ensures that doesn't happen.
  // See https://github.com/facebook/regenerator/issues/274 for more details.
  Gp[iteratorSymbol] = function() {
    return this;
  };

  Gp.toString = function() {
    return "[object Generator]";
  };

  function pushTryEntry(locs) {
    var entry = { tryLoc: locs[0] };

    if (1 in locs) {
      entry.catchLoc = locs[1];
    }

    if (2 in locs) {
      entry.finallyLoc = locs[2];
      entry.afterLoc = locs[3];
    }

    this.tryEntries.push(entry);
  }

  function resetTryEntry(entry) {
    var record = entry.completion || {};
    record.type = "normal";
    delete record.arg;
    entry.completion = record;
  }

  function Context(tryLocsList) {
    // The root entry object (effectively a try statement without a catch
    // or a finally block) gives us a place to store values thrown from
    // locations where there is no enclosing try statement.
    this.tryEntries = [{ tryLoc: "root" }];
    tryLocsList.forEach(pushTryEntry, this);
    this.reset(true);
  }

  runtime.keys = function(object) {
    var keys = [];
    for (var key in object) {
      keys.push(key);
    }
    keys.reverse();

    // Rather than returning an object with a next method, we keep
    // things simple and return the next function itself.
    return function next() {
      while (keys.length) {
        var key = keys.pop();
        if (key in object) {
          next.value = key;
          next.done = false;
          return next;
        }
      }

      // To avoid creating an additional object, we just hang the .value
      // and .done properties off the next function object itself. This
      // also ensures that the minifier will not anonymize the function.
      next.done = true;
      return next;
    };
  };

  function values(iterable) {
    if (iterable) {
      var iteratorMethod = iterable[iteratorSymbol];
      if (iteratorMethod) {
        return iteratorMethod.call(iterable);
      }

      if (typeof iterable.next === "function") {
        return iterable;
      }

      if (!isNaN(iterable.length)) {
        var i = -1, next = function next() {
          while (++i < iterable.length) {
            if (hasOwn.call(iterable, i)) {
              next.value = iterable[i];
              next.done = false;
              return next;
            }
          }

          next.value = undefined;
          next.done = true;

          return next;
        };

        return next.next = next;
      }
    }

    // Return an iterator with no values.
    return { next: doneResult };
  }
  runtime.values = values;

  function doneResult() {
    return { value: undefined, done: true };
  }

  Context.prototype = {
    constructor: Context,

    reset: function(skipTempReset) {
      this.prev = 0;
      this.next = 0;
      // Resetting context._sent for legacy support of Babel's
      // function.sent implementation.
      this.sent = this._sent = undefined;
      this.done = false;
      this.delegate = null;

      this.method = "next";
      this.arg = undefined;

      this.tryEntries.forEach(resetTryEntry);

      if (!skipTempReset) {
        for (var name in this) {
          // Not sure about the optimal order of these conditions:
          if (name.charAt(0) === "t" &&
              hasOwn.call(this, name) &&
              !isNaN(+name.slice(1))) {
            this[name] = undefined;
          }
        }
      }
    },

    stop: function() {
      this.done = true;

      var rootEntry = this.tryEntries[0];
      var rootRecord = rootEntry.completion;
      if (rootRecord.type === "throw") {
        throw rootRecord.arg;
      }

      return this.rval;
    },

    dispatchException: function(exception) {
      if (this.done) {
        throw exception;
      }

      var context = this;
      function handle(loc, caught) {
        record.type = "throw";
        record.arg = exception;
        context.next = loc;

        if (caught) {
          // If the dispatched exception was caught by a catch block,
          // then let that catch block handle the exception normally.
          context.method = "next";
          context.arg = undefined;
        }

        return !! caught;
      }

      for (var i = this.tryEntries.length - 1; i >= 0; --i) {
        var entry = this.tryEntries[i];
        var record = entry.completion;

        if (entry.tryLoc === "root") {
          // Exception thrown outside of any try block that could handle
          // it, so set the completion value of the entire function to
          // throw the exception.
          return handle("end");
        }

        if (entry.tryLoc <= this.prev) {
          var hasCatch = hasOwn.call(entry, "catchLoc");
          var hasFinally = hasOwn.call(entry, "finallyLoc");

          if (hasCatch && hasFinally) {
            if (this.prev < entry.catchLoc) {
              return handle(entry.catchLoc, true);
            } else if (this.prev < entry.finallyLoc) {
              return handle(entry.finallyLoc);
            }

          } else if (hasCatch) {
            if (this.prev < entry.catchLoc) {
              return handle(entry.catchLoc, true);
            }

          } else if (hasFinally) {
            if (this.prev < entry.finallyLoc) {
              return handle(entry.finallyLoc);
            }

          } else {
            throw new Error("try statement without catch or finally");
          }
        }
      }
    },

    abrupt: function(type, arg) {
      for (var i = this.tryEntries.length - 1; i >= 0; --i) {
        var entry = this.tryEntries[i];
        if (entry.tryLoc <= this.prev &&
            hasOwn.call(entry, "finallyLoc") &&
            this.prev < entry.finallyLoc) {
          var finallyEntry = entry;
          break;
        }
      }

      if (finallyEntry &&
          (type === "break" ||
           type === "continue") &&
          finallyEntry.tryLoc <= arg &&
          arg <= finallyEntry.finallyLoc) {
        // Ignore the finally entry if control is not jumping to a
        // location outside the try/catch block.
        finallyEntry = null;
      }

      var record = finallyEntry ? finallyEntry.completion : {};
      record.type = type;
      record.arg = arg;

      if (finallyEntry) {
        this.method = "next";
        this.next = finallyEntry.finallyLoc;
        return ContinueSentinel;
      }

      return this.complete(record);
    },

    complete: function(record, afterLoc) {
      if (record.type === "throw") {
        throw record.arg;
      }

      if (record.type === "break" ||
          record.type === "continue") {
        this.next = record.arg;
      } else if (record.type === "return") {
        this.rval = this.arg = record.arg;
        this.method = "return";
        this.next = "end";
      } else if (record.type === "normal" && afterLoc) {
        this.next = afterLoc;
      }

      return ContinueSentinel;
    },

    finish: function(finallyLoc) {
      for (var i = this.tryEntries.length - 1; i >= 0; --i) {
        var entry = this.tryEntries[i];
        if (entry.finallyLoc === finallyLoc) {
          this.complete(entry.completion, entry.afterLoc);
          resetTryEntry(entry);
          return ContinueSentinel;
        }
      }
    },

    "catch": function(tryLoc) {
      for (var i = this.tryEntries.length - 1; i >= 0; --i) {
        var entry = this.tryEntries[i];
        if (entry.tryLoc === tryLoc) {
          var record = entry.completion;
          if (record.type === "throw") {
            var thrown = record.arg;
            resetTryEntry(entry);
          }
          return thrown;
        }
      }

      // The context.catch method must only be called with a location
      // argument that corresponds to a known catch block.
      throw new Error("illegal catch attempt");
    },

    delegateYield: function(iterable, resultName, nextLoc) {
      this.delegate = {
        iterator: values(iterable),
        resultName: resultName,
        nextLoc: nextLoc
      };

      if (this.method === "next") {
        // Deliberately forget the last sent value so that we don't
        // accidentally pass it on to the delegate.
        this.arg = undefined;
      }

      return ContinueSentinel;
    }
  };
})(
  // In sloppy mode, unbound `this` refers to the global object, fallback to
  // Function constructor if we're in global strict mode. That is sadly a form
  // of indirect eval which violates Content Security Policy.
  (function() { return this })() || Function("return this")()
);


/***/ }),
/* 141 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, '__esModule', { value: true });

var error = function (message) {
  function E() {
    this.message = message;
  }

  E.prototype = new Error();
  E.prototype.name = 'InvalidCharacterError';
  E.prototype.code = 5;

  return E;
};

var chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/=';

// btoa polyfill for IE<10 courtesy https://gist.github.com/nignag/999166

var E = error('The string to be encoded contains characters out of range');

var _btoa = typeof btoa !== 'undefined'
/* istanbul ignore next */
? btoa : function (input) {
  var str = String(input);
  var output = '';

  for (
  // initialize result and counter
  var block, charCode, idx = 0, map = chars;
  // if the next str index does not exist:
  //   change the mapping table to "="
  //   check if d has no fractional digits
  str.charAt(idx | 0) || (map = '=', idx % 1);
  // "8 - idx % 1 * 8" generates the sequence 2, 4, 6, 8
  output += map.charAt(63 & block >> 8 - idx % 1 * 8)) {

    charCode = str.charCodeAt(idx += 3 / 4);
    if (charCode > 0xFF) {
      throw new E();
    }

    block = block << 8 | charCode;
  }

  return output;
};

var utf8 = function (input) {
  return encodeURIComponent(input).replace(/%([0-9A-F]{2})/g, function (match, p1) {
    return String.fromCharCode('0x' + p1);
  });
};

var btoa$1 = (function (input) {
  return _btoa(utf8(input));
});

var E$1 = error('The string to be decoded is not correctly encoded');

var _atob = typeof atob !== 'undefined' ? atob : function (input) {

  var str = String(input).replace(/[=]+$/, '');

  if (str.length % 4 == 1) {
    throw new E$1();
  }

  var output = '';

  for (
  // initialize result and counters
  var bc = 0, bs, buffer, idx = 0;
  // get next character
  buffer = str.charAt(idx++);
  // character found in table? initialize bit storage and add its ascii value;
  ~buffer && (bs = bc % 4 ? bs * 64 + buffer : buffer,
  // and if not first of each 4 characters,
  // convert the first 8 bits to one ascii character
  bc++ % 4) ? output += String.fromCharCode(255 & bs >> (-2 * bc & 6)) : 0) {
    // try to find character in table (0-63, not found => -1)
    buffer = chars.indexOf(buffer);
  }

  return output;
};

var utf16 = function (input) {
  return decodeURIComponent(input.split('').map(function (c) {
    return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
  }).join(''));
};

var atob$1 = (function (input) {
  return utf16(_atob(input));
});

exports.btoa = btoa$1;
exports.atob = atob$1;


/***/ }),
/* 142 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.parseOGP = exports.parseBT = exports.percentScrolled = exports.documentHeight = exports.browserHeight = exports._pixelsScrolled = exports.resolveRelativeUrl = exports.parseResourceProp = exports.parseSchema = exports.parseBasicMeta = exports.parseTwitter = undefined;

var _getIterator2 = __webpack_require__(27);

var _getIterator3 = _interopRequireDefault(_getIterator2);

var _assign = __webpack_require__(28);

var _assign2 = _interopRequireDefault(_assign);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var _getAllElementsWithAttribute = function _getAllElementsWithAttribute(attribute) {
    var matchingElements = [];
    var allElements = document.getElementsByTagName('*');

    // TODO: make this more functional
    for (var i = 0; i < allElements.length; i++) {
        if (allElements[i].getAttribute(attribute)) {
            matchingElements.push(allElements[i]);
        }
    }

    return matchingElements;
};

var _parseMeta = function _parseMeta(pattern) {
    var key = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : 'property';

    var elements = document.getElementsByTagName('meta');
    var data = {};

    // TODO: make this more functional
    // WTF: why is this going in reverse?
    for (var i = elements.length - 1; i >= 0; i--) {
        var property = elements[i].getAttribute && elements[i].getAttribute(key);
        if (property && property.match(pattern)) {
            data[property.replace(pattern, '')] = elements[i].getAttribute('content');
        }
    }
    return data;
};

var parseBt = function parseBt() {
    return (0, _assign2["default"])(_parseMeta('bt:', 'name'), _parseMeta('bt:'));
};

var parseOgp = function parseOgp() {
    return _parseMeta('og:');
};

var parseTwitter = exports.parseTwitter = function parseTwitter() {
    return _parseMeta('twitter:', 'name');
};

var parseBasicMeta = exports.parseBasicMeta = function parseBasicMeta() {
    var getCanonicalUrl = function getCanonicalUrl() {
        var links = document.getElementsByTagName('link');
        for (var i = links.length - 1; i >= 0; i--) {
            var rel = links[i].getAttribute('rel');
            if (rel === 'canonical') {
                return links[i].getAttribute('href');
            }
        }
        return null;
    };

    return {
        url: getCanonicalUrl()
    };
};

var parseSchema = exports.parseSchema = function parseSchema() {
    var elements = _getAllElementsWithAttribute('itemprop');
    var data = {};

    var selectText = function selectText(element) {
        return element.textContent || element.innerText || element.getAttribute('content');
    };
    // TODO: make this more functional
    // WTF: why is this in reverse?
    for (var i = elements.length - 1; i >= 0; i--) {
        data[elements[i].getAttribute('itemprop')] = selectText(elements[i]);
    }

    return data;
};

var parseResourceProp = exports.parseResourceProp = function parseResourceProp(attribute, resourceSelectors) {
    if (resourceSelectors && resourceSelectors[attribute]) {
        var selectors = resourceSelectors[attribute].split(',');
        var _iteratorNormalCompletion = true;
        var _didIteratorError = false;
        var _iteratorError = undefined;

        try {
            for (var _iterator = (0, _getIterator3["default"])(selectors), _step; !(_iteratorNormalCompletion = (_step = _iterator.next()).done); _iteratorNormalCompletion = true) {
                var _selector = _step.value;

                var element = document.querySelector(_selector);
                if (element) {
                    return element.getAttribute('content') || element.textContent.trim();
                }
            }
        } catch (err) {
            _didIteratorError = true;
            _iteratorError = err;
        } finally {
            try {
                if (!_iteratorNormalCompletion && _iterator["return"]) {
                    _iterator["return"]();
                }
            } finally {
                if (_didIteratorError) {
                    throw _iteratorError;
                }
            }
        }
    }
    var selector = resourceSelectors && resourceSelectors[attribute];
    if (selector) {
        var _element = document.querySelector(selector);

        if (_element) {
            return _element.getAttribute('content') || _element.textContent.trim();
        }
    }
    return null;
};

var resolveRelativeUrl = exports.resolveRelativeUrl = function resolveRelativeUrl(url) {
    var div = document.createElement('div');
    div.innerHTML = '<a></a>';
    div.firstChild.href = url; // ensures href is properly escaped
    div.innerHTML = div.innerHTML; // Run the current innerHTML back through the parser

    return div.firstChild.href;
};

var _pixelsScrolled = exports._pixelsScrolled = function _pixelsScrolled() {
    return window.pageYOffset || (document.documentElement || document.body.parentNode || document.body).scrollTop;
};

var browserHeight = exports.browserHeight = function browserHeight() {
    return window.innerHeight || (document.documentElement || document.body).clientHeight;
};

var documentHeight = exports.documentHeight = function documentHeight() {
    var doc = document;
    return Math.max(doc.body.scrollHeight, doc.documentElement.scrollHeight, doc.body.offsetHeight, doc.documentElement.offsetHeight, doc.body.clientHeight, doc.documentElement.clientHeight);
};

var percentScrolled = exports.percentScrolled = function percentScrolled(maxScrollablePixels) {
    return Math.floor(_pixelsScrolled() / maxScrollablePixels * 100);
};

exports.parseBT = parseBt;
exports.parseOGP = parseOgp;

/***/ }),
/* 143 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
var VERSION = exports.VERSION = '5.6.1';

var libraryConfig = {
    debug: true,
    apiEventHost: 'https://events.api.boomtrain.com',
    peopleHost: 'https://people.api.boomtrain.com',
    onsiteHost: 'https://onsite.boomtrain.net/osrs',
    activeSelectors: 'https://onsite.boomtrain.net/active_selectors',
    useXhr: window.XMLHttpRequest && 'withCredentials' in new XMLHttpRequest(),
    trackByUrl: false,
    autoTrack: false,
    resourceSelectors: { 'tags': 'props.tags', 'title': 'title', 'resource-type': 'resource_type', 'description': 'description', 'modDate': 'modified_at', 'keywords': 'props.keywords', 'body': 'body', 'thumbnail': 'thumbnail', 'isUnavailable': 'isUnavailable', 'pubDate': 'published_at', 'authors': 'props.author', 'isBlacklisted': 'isBlacklisted', 'url': 'url' },
    test: false,
    scrollTrackLevels: [25, 50, 75, 100]
};

exports.CONFIG = libraryConfig;

/***/ }),
/* 144 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.Console = undefined;

var _classCallCheck2 = __webpack_require__(29);

var _classCallCheck3 = _interopRequireDefault(_classCallCheck2);

var _createClass2 = __webpack_require__(30);

var _createClass3 = _interopRequireDefault(_createClass2);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var Console = exports.Console = function () {
    function Console(windowConsole) {
        var debug = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : false;
        (0, _classCallCheck3["default"])(this, Console);

        this._debug = debug;
        this._windowConsole = windowConsole;
    }

    (0, _createClass3["default"])(Console, [{
        key: 'log',
        value: function log() {
            var _windowConsole;

            if (!this._debug || !this._windowConsole) return;

            (_windowConsole = this._windowConsole).log.apply(_windowConsole, arguments);
        }
    }, {
        key: 'error',
        value: function error() {
            var _windowConsole2;

            if (!this._debug || !this._windowConsole) return;

            (_windowConsole2 = this._windowConsole).log.apply(_windowConsole2, arguments);
        }
    }, {
        key: 'critical',
        value: function critical() {
            var _windowConsole3;

            if (!this._windowConsole) return;

            (_windowConsole3 = this._windowConsole).log.apply(_windowConsole3, arguments);
        }
    }]);
    return Console;
}();

/***/ }),
/* 145 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.Identity = exports.LEGACY_IDENTITY_COOKIE_NAME = exports.DEFAULT_IDENTITY_EXPIRE = exports.IDENTITY_KEY = undefined;

var _set = __webpack_require__(71);

var _set2 = _interopRequireDefault(_set);

var _isInteger = __webpack_require__(146);

var _isInteger2 = _interopRequireDefault(_isInteger);

var _keys = __webpack_require__(21);

var _keys2 = _interopRequireDefault(_keys);

var _map2 = __webpack_require__(17);

var _map3 = _interopRequireDefault(_map2);

var _assign = __webpack_require__(28);

var _assign2 = _interopRequireDefault(_assign);

var _classCallCheck2 = __webpack_require__(29);

var _classCallCheck3 = _interopRequireDefault(_classCallCheck2);

var _createClass2 = __webpack_require__(30);

var _createClass3 = _interopRequireDefault(_createClass2);

var _cookie = __webpack_require__(72);

var cookie = _interopRequireWildcard(_cookie);

var _url = __webpack_require__(46);

var _common = __webpack_require__(31);

var common = _interopRequireWildcard(_common);

function _interopRequireWildcard(obj) { if (obj && obj.__esModule) { return obj; } else { var newObj = {}; if (obj != null) { for (var key in obj) { if (Object.prototype.hasOwnProperty.call(obj, key)) newObj[key] = obj[key]; } } newObj["default"] = obj; return newObj; } }

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var IDENTITY_KEY = exports.IDENTITY_KEY = '_bti';
var DEFAULT_IDENTITY_EXPIRE = exports.DEFAULT_IDENTITY_EXPIRE = 365 * 24 * 60 * 60 * 1000;
var LEGACY_IDENTITY_COOKIE_NAME = exports.LEGACY_IDENTITY_COOKIE_NAME = 'btIdentify';

var Identity = exports.Identity = function () {
    function Identity() {
        var options = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};
        (0, _classCallCheck3["default"])(this, Identity);

        // TODO: move this to a `Map`
        options = (0, _assign2["default"])({
            key: IDENTITY_KEY,
            expire: DEFAULT_IDENTITY_EXPIRE
        }, options);

        this.key = options.key;
        this.expire = options.expire;
        // TODO: move this to a `Map`
        this.props = {
            bsin: ''
        };
        this._load();

        if (this.props.bsin === '' && typeof this.props.app_member_id === 'undefined') {
            this.props = { bsin: '' };
            if (!cookie.get(LEGACY_IDENTITY_COOKIE_NAME)) {
                cookie.set(LEGACY_IDENTITY_COOKIE_NAME, Identity._userId(), DEFAULT_IDENTITY_EXPIRE, true);
            }
        }

        this._save();

        this._qsIdentity = null;
    }

    (0, _createClass3["default"])(Identity, [{
        key: 'bsin',
        value: function bsin() {
            return this.props.bsin;
        }
    }, {
        key: 'userId',
        value: function userId() {
            return this.props['app_member_id'];
        }
    }, {
        key: 'currentId',
        value: function currentId() {
            return this.props['app_member_id'] || this.props.bsin || cookie.get(LEGACY_IDENTITY_COOKIE_NAME);
        }
    }, {
        key: 'parseIdentity',
        value: function parseIdentity(identity) {
            var _this = this;

            var asBase64 = arguments.length > 1 && arguments[1] !== undefined ? arguments[1] : false;

            // There are 3 (!) ways to get identity.
            // 1a. Passed in as a user id in the argument (by the customer's web page)
            // 1b. Passed in as a user identity blob in the argument
            // 2. From the cookie
            // 3. From the query string
            var identityMap = new _map3["default"]();

            if (common.isObject(identity)) {
                identityMap = new _map3["default"]((0, _keys2["default"])(identity).map(function (key) {
                    return [key, identity[key]];
                }));
            } else if (common.isString(identity) || (0, _isInteger2["default"])(identity)) {
                identityMap.set('app_member_id', String(identity));
            }

            // handle customer-supplied `user_id` (ENG-463)
            if (identityMap.has('user_id')) {
                var userId = identityMap.get('user_id');
                if (common.isString(userId) || (0, _isInteger2["default"])(userId)) {
                    identityMap.set('app_member_id', String(userId));
                }
            }

            // hack-ish fix: option to indicate whether query params should be used to identify users.
            // see CUST-1852
            var ignoreQuery = identityMap.get('_ignoreQuery');

            // Drop everything that we're not keen on keeping any more
            var interestingKeys = new _set2["default"](['bsin', 'new_bsin', 'app_member_id', 'email']);
            identityMap.forEach(function (value, key, map) {
                if (!interestingKeys.has(key)) {
                    map["delete"](key);
                }
            });
            if (identityMap.has('new_bsin') && identityMap.get('new_bsin') == this.props.bsin) {
                identityMap["delete"]('new_bsin');
            }

            // Temporary fix for integer appMemberIds.
            // Pass btIdentify along to `/identify` so it can be aliased if need be
            var btIdentify = cookie.get(LEGACY_IDENTITY_COOKIE_NAME);
            if ((0, _isInteger2["default"])(identity) && btIdentify && !identityMap.has('bsin') && !identityMap.has('new_bsin')) {
                identityMap.set('btIdentify', btIdentify);
            }

            // convert user_id to app_member_id for backwards compatibility
            var cookieIdentity = new _map3["default"]();
            (0, _keys2["default"])(this.props).forEach(function (key) {
                cookieIdentity.set(key, _this.props[key]);
            });
            if (cookieIdentity.has('user_id')) {
                cookieIdentity.set('app_member_id', cookieIdentity.get('user_id'));
                cookieIdentity["delete"]('user_id');
            }

            var providedIdentity = new _map3["default"]();
            identityMap.forEach(function (value, key, _map) {
                if (key === 'email' || key === 'app_member_id') {
                    providedIdentity.set(key, value);
                }
            });
            if (providedIdentity.size === 0 && !ignoreQuery) {
                // Parsing the query string is the new way forward for identity (apparently)
                providedIdentity = this._getQueryStringIdentity();
            }
            // new_bsin kept for backwards compatibility and treated
            // as querystring.bsin
            if (identityMap.has('new_bsin')) {
                providedIdentity.set('bsin', identityMap.get('new_bsin'));
            }

            var payload = {
                cookie: common.mapToObject(cookieIdentity),
                querystring: common.mapToObject(providedIdentity)
            };

            var jsonData = common.JSONEncode(payload);
            var encodedData = asBase64 ? common.base64Encode(jsonData) : jsonData;

            return encodedData;
        }
    }, {
        key: '_getQueryStringIdentity',
        value: function _getQueryStringIdentity() {
            var _this2 = this;

            if (this._qsIdentity) return this._qsIdentity;

            this._qsIdentity = new _map3["default"]();

            var qsIdentity = (0, _url.parseQueryString)();
            var identityKeys = new _set2["default"](['bt_bsin', 'bt_user_id', 'bt_app_member_id', 'bt_email', 'bt_ee']);
            // strip prefix off `identityKeys` and delete all the others
            qsIdentity.forEach(function (value, key, _map) {
                if (identityKeys.has(key)) {
                    _this2._qsIdentity.set(key.replace('bt_', ''), value);
                }
            });

            if (this._qsIdentity.has('user_id')) {
                this._qsIdentity.set('app_member_id', this._qsIdentity.get('user_id'));
                this._qsIdentity["delete"]('user_id');
            }

            return this._qsIdentity;
        }
    }, {
        key: 'remove',
        value: function remove() {
            cookie.remove(this.key, false);
            cookie.remove(this.key, true);
        }
    }, {
        key: 'update',
        value: function update(props) {
            this._replace(props);
            this._save();

            // TODO: figure out if we need this code:
            // Backwards compatibility for aliasing the old way.
            // We infer the old way is being used when no bsin or app_member_id was returned.
            // if (identity.new_bsin && res && !res.bsin && !res.app_member_id) {
            //     var year = 365 * 24 * 60 * 60 * 1000
            //     _.cookie.set('btIdentify', identity.new_bsin, year, true)
            // }
        }
    }, {
        key: '_replace',
        value: function _replace(props) {
            if (!common.isObject(props)) {
                console.log(new Error('Identity properties must be an object'));
            }

            this.props = (0, _assign2["default"])({}, props);
        }
    }, {
        key: '_load',
        value: function _load() {
            var rawCookie = cookie.get(this.key);
            if (rawCookie) {
                try {
                    var props = common.JSONDecode(rawCookie) || {};

                    if (props && (0, _keys2["default"])(props).length) {
                        this._replace(props);
                    }
                } catch (error) {
                    console.log('No valid cookie data');
                }
            }
        }
    }, {
        key: '_save',
        value: function _save() {
            cookie.set(this.key, common.JSONEncode(this.props), this.expire, true);
        }
    }], [{
        key: '_userId',
        value: function _userId() {
            var d = new Date().getTime();
            var uuid = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function (c) {
                var r = (d + Math.random() * 16) % 16 | 0;
                d = Math.floor(d / 16);
                return (c === 'x' ? r : r & 0x7 | 0x8).toString(16);
            });

            return uuid;
        }
    }]);
    return Identity;
}();

/***/ }),
/* 146 */
/***/ (function(module, exports, __webpack_require__) {

module.exports = { "default": __webpack_require__(147), __esModule: true };

/***/ }),
/* 147 */
/***/ (function(module, exports, __webpack_require__) {

__webpack_require__(148);
module.exports = __webpack_require__(0).Number.isInteger;


/***/ }),
/* 148 */
/***/ (function(module, exports, __webpack_require__) {

// 20.1.2.3 Number.isInteger(number)
var $export = __webpack_require__(1);

$export($export.S, 'Number', { isInteger: __webpack_require__(149) });


/***/ }),
/* 149 */
/***/ (function(module, exports, __webpack_require__) {

// 20.1.2.3 Number.isInteger(number)
var isObject = __webpack_require__(4);
var floor = Math.floor;
module.exports = function isInteger(it) {
  return !isObject(it) && isFinite(it) && floor(it) === it;
};


/***/ }),
/* 150 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.sendRequest = undefined;

var _map = __webpack_require__(17);

var _map2 = _interopRequireDefault(_map);

var _promise = __webpack_require__(64);

var _promise2 = _interopRequireDefault(_promise);

var _url = __webpack_require__(46);

var _common = __webpack_require__(31);

var common = _interopRequireWildcard(_common);

function _interopRequireWildcard(obj) { if (obj && obj.__esModule) { return obj; } else { var newObj = {}; if (obj != null) { for (var key in obj) { if (Object.prototype.hasOwnProperty.call(obj, key)) newObj[key] = obj[key]; } } newObj["default"] = obj; return newObj; } }

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var callbackCount = 0;

// Adapted from https://github.com/alexbardas/jsonp-promise
// TODO: don't automatically use `_bt`
var asJsonp = function asJsonp(url, options) {

    var prefix = 'cb_';
    var id = prefix + callbackCount++;
    if (common.isUndefined(window._bt.callbacks)) {
        window._bt.callbacks = {};
        window.OK = function () {};
    }
    var callbacks = window._bt.callbacks;

    var script = null;
    var timer = null;

    var noop = function noop() {};

    var cleanup = function cleanup() {
        if (script && script.parentNode) {
            script.parentNode.removeChild(script);
        }
        callbacks[id] = noop;

        if (timer) {
            clearTimeout(timer);
        }
    };

    var hasCallback = options.get('callback') || false;
    var timeout = options.get('timeout');
    var target = document.getElementsByTagName('script')[0] || document.head;

    var promise = new _promise2["default"](function (resolve, reject) {
        if (timeout) {
            timer = setTimeout(function () {
                cleanup();
                if (hasCallback) {
                    reject(new Error('Timeout'));
                } else {
                    resolve('Timeout');
                }
            }, timeout);
        }

        var createCallback = function createCallback(callbackId) {
            callbacks[callbackId] = function (data) {
                cleanup();
                resolve([data, url]);
            };
            return encodeURIComponent('_bt.callbacks.' + callbackId);
        };

        url += (~url.indexOf('?') ? '&' : '?') + 'callback=';
        url += hasCallback ? createCallback(id) : '_bt._noop';
        url = url.replace('?&', '?');
        if (!/app=/.test(url)) url += '&app=' + options.get('siteId');

        script = document.createElement('script');
        script.type = 'text/javascript';
        script.async = true;
        script.defer = true;
        script.src = url;
        target.parentNode.insertBefore(script, target);
    });

    return promise;
};

var sendRequest = exports.sendRequest = function sendRequest(siteId, url, data, useXhr) {
    var jsonpCallback = arguments.length > 4 && arguments[4] !== undefined ? arguments[4] : true;
    var timeout = arguments.length > 5 && arguments[5] !== undefined ? arguments[5] : 2000;


    url += '?' + (0, _url.buildQueryString)(data, siteId);

    if (useXhr) {
        return new _promise2["default"](function (resolve, reject) {
            var req = new XMLHttpRequest();

            req.open('GET', url, true);
            req.timeout = timeout;

            req.onreadystatechange = function () {
                if (req.readyState != 4) return;
                if (req.status === 200 || req.status === 201) {
                    var decodedResponse = '';
                    try {
                        decodedResponse = common.JSONDecode(req.responseText);
                    } catch (error) {
                        decodedResponse = req.responseText;
                    }
                    resolve([decodedResponse, url]);
                } else {
                    reject(Error(req.statusText));
                }
            };

            req.onerror = function () {
                reject(Error('Network error'));
            };

            req.ontimeout = function () {
                reject(Error('Request timed out'));
            };

            req.send();
        });
    } else {
        var options = new _map2["default"]();
        options.set('timeout', timeout);
        options.set('siteId', siteId);
        options.set('callback', jsonpCallback);
        return asJsonp(url, options);
    }
};

/***/ }),
/* 151 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";


Object.defineProperty(exports, "__esModule", {
    value: true
});
exports.Session = exports.DEFAULT_SESSION_EXPIRE = exports.SESSION_KEY = undefined;

var _assign = __webpack_require__(28);

var _assign2 = _interopRequireDefault(_assign);

var _classCallCheck2 = __webpack_require__(29);

var _classCallCheck3 = _interopRequireDefault(_classCallCheck2);

var _createClass2 = __webpack_require__(30);

var _createClass3 = _interopRequireDefault(_createClass2);

var _cookie = __webpack_require__(72);

var cookie = _interopRequireWildcard(_cookie);

function _interopRequireWildcard(obj) { if (obj && obj.__esModule) { return obj; } else { var newObj = {}; if (obj != null) { for (var key in obj) { if (Object.prototype.hasOwnProperty.call(obj, key)) newObj[key] = obj[key]; } } newObj["default"] = obj; return newObj; } }

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var SESSION_KEY = exports.SESSION_KEY = '_bts';
var DEFAULT_SESSION_EXPIRE = exports.DEFAULT_SESSION_EXPIRE = 60 * 60 * 1000;

var Session = exports.Session = function () {
    function Session() {
        var options = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : {};
        (0, _classCallCheck3["default"])(this, Session);

        options = (0, _assign2["default"])({
            key: SESSION_KEY,
            expire: DEFAULT_SESSION_EXPIRE
        }, options);
        this._isNewSession = false;

        this.key = options.key;
        this.expire = options.expire;

        this._load();

        if (!this.id) {
            this._isNewSession = true;
            this.id = Session._sessionId();
        }

        this._save();
    }

    (0, _createClass3["default"])(Session, [{
        key: 'remove',
        value: function remove() {
            cookie.remove(this.key, false);
            cookie.remove(this.key, true);
        }
    }, {
        key: 'isNew',
        value: function isNew() {
            if (this._isNewSession) {
                this._isNewSession = false;
                return true;
            }
            return false;
        }
    }, {
        key: '_load',
        value: function _load() {
            var id = cookie.get(this.key);

            if (id) {
                this.id = id;
            }
        }

        // TODO: put this in a common file

    }, {
        key: '_save',
        value: function _save() {
            cookie.set(this.key, this.id, this.expire, true);
        }
    }], [{
        key: '_sessionId',
        value: function _sessionId() {
            var d = new Date().getTime();
            var uuid = 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, function (c) {
                var r = (d + Math.random() * 16) % 16 | 0;
                d = Math.floor(d / 16);
                return (c === 'x' ? r : r & 0x7 | 0x8).toString(16);
            });

            return uuid;
        }
    }]);
    return Session;
}();

/***/ }),
/* 152 */
/***/ (function(module, exports, __webpack_require__) {

"use strict";
/* eslint no-undefined:off */

// Based on https://github.com/blueimp/JavaScript-MD5
// Fixed for eslint rules

/*
 * Add integers, wrapping at 2^32. This uses 16-bit operations internally
 * to work around bugs in some JS interpreters.
 */

Object.defineProperty(exports, "__esModule", {
    value: true
});

var _from = __webpack_require__(70);

var _from2 = _interopRequireDefault(_from);

var _slicedToArray2 = __webpack_require__(20);

var _slicedToArray3 = _interopRequireDefault(_slicedToArray2);

function _interopRequireDefault(obj) { return obj && obj.__esModule ? obj : { "default": obj }; }

var safeAdd = function safeAdd(x, y) {
    var lsw = (x & 0xFFFF) + (y & 0xFFFF);
    return (x >> 16) + (y >> 16) + (lsw >> 16) << 16 | lsw & 0xFFFF;
};

/*
 * Bitwise rotate a 32-bit number to the left.
 */
var bitRotateLeft = function bitRotateLeft(num, cnt) {
    return num << cnt | num >>> 32 - cnt;
};

/*
 * These functions implement the four basic operations the algorithm uses.
 */
var md5cmn = function md5cmn(q, a, b, x, s, t) {
    return safeAdd(bitRotateLeft(safeAdd(safeAdd(a, q), safeAdd(x, t)), s), b);
},
    md5ff = function md5ff(a, b, c, d, x, s, t) {
    return md5cmn(b & c | ~b & d, a, b, x, s, t);
},
    md5gg = function md5gg(a, b, c, d, x, s, t) {
    return md5cmn(b & d | c & ~d, a, b, x, s, t);
},
    md5hh = function md5hh(a, b, c, d, x, s, t) {
    return md5cmn(b ^ c ^ d, a, b, x, s, t);
},
    md5ii = function md5ii(a, b, c, d, x, s, t) {
    return md5cmn(c ^ (b | ~d), a, b, x, s, t);
};

var firstChunk = function firstChunk(chunks, x, i) {
    var _chunks = (0, _slicedToArray3["default"])(chunks, 4),
        a = _chunks[0],
        b = _chunks[1],
        c = _chunks[2],
        d = _chunks[3];

    a = md5ff(a, b, c, d, x[i + 0], 7, -680876936);
    d = md5ff(d, a, b, c, x[i + 1], 12, -389564586);
    c = md5ff(c, d, a, b, x[i + 2], 17, 606105819);
    b = md5ff(b, c, d, a, x[i + 3], 22, -1044525330);

    a = md5ff(a, b, c, d, x[i + 4], 7, -176418897);
    d = md5ff(d, a, b, c, x[i + 5], 12, 1200080426);
    c = md5ff(c, d, a, b, x[i + 6], 17, -1473231341);
    b = md5ff(b, c, d, a, x[i + 7], 22, -45705983);

    a = md5ff(a, b, c, d, x[i + 8], 7, 1770035416);
    d = md5ff(d, a, b, c, x[i + 9], 12, -1958414417);
    c = md5ff(c, d, a, b, x[i + 10], 17, -42063);
    b = md5ff(b, c, d, a, x[i + 11], 22, -1990404162);

    a = md5ff(a, b, c, d, x[i + 12], 7, 1804603682);
    d = md5ff(d, a, b, c, x[i + 13], 12, -40341101);
    c = md5ff(c, d, a, b, x[i + 14], 17, -1502002290);
    b = md5ff(b, c, d, a, x[i + 15], 22, 1236535329);

    return [a, b, c, d];
};

var secondChunk = function secondChunk(chunks, x, i) {
    var _chunks2 = (0, _slicedToArray3["default"])(chunks, 4),
        a = _chunks2[0],
        b = _chunks2[1],
        c = _chunks2[2],
        d = _chunks2[3];

    a = md5gg(a, b, c, d, x[i + 1], 5, -165796510);
    d = md5gg(d, a, b, c, x[i + 6], 9, -1069501632);
    c = md5gg(c, d, a, b, x[i + 11], 14, 643717713);
    b = md5gg(b, c, d, a, x[i], 20, -373897302);

    a = md5gg(a, b, c, d, x[i + 5], 5, -701558691);
    d = md5gg(d, a, b, c, x[i + 10], 9, 38016083);
    c = md5gg(c, d, a, b, x[i + 15], 14, -660478335);
    b = md5gg(b, c, d, a, x[i + 4], 20, -405537848);

    a = md5gg(a, b, c, d, x[i + 9], 5, 568446438);
    d = md5gg(d, a, b, c, x[i + 14], 9, -1019803690);
    c = md5gg(c, d, a, b, x[i + 3], 14, -187363961);
    b = md5gg(b, c, d, a, x[i + 8], 20, 1163531501);

    a = md5gg(a, b, c, d, x[i + 13], 5, -1444681467);
    d = md5gg(d, a, b, c, x[i + 2], 9, -51403784);
    c = md5gg(c, d, a, b, x[i + 7], 14, 1735328473);
    b = md5gg(b, c, d, a, x[i + 12], 20, -1926607734);

    return [a, b, c, d];
};

var thirdChunk = function thirdChunk(chunks, x, i) {
    var _chunks3 = (0, _slicedToArray3["default"])(chunks, 4),
        a = _chunks3[0],
        b = _chunks3[1],
        c = _chunks3[2],
        d = _chunks3[3];

    a = md5hh(a, b, c, d, x[i + 5], 4, -378558);
    d = md5hh(d, a, b, c, x[i + 8], 11, -2022574463);
    c = md5hh(c, d, a, b, x[i + 11], 16, 1839030562);
    b = md5hh(b, c, d, a, x[i + 14], 23, -35309556);

    a = md5hh(a, b, c, d, x[i + 1], 4, -1530992060);
    d = md5hh(d, a, b, c, x[i + 4], 11, 1272893353);
    c = md5hh(c, d, a, b, x[i + 7], 16, -155497632);
    b = md5hh(b, c, d, a, x[i + 10], 23, -1094730640);

    a = md5hh(a, b, c, d, x[i + 13], 4, 681279174);
    d = md5hh(d, a, b, c, x[i], 11, -358537222);
    c = md5hh(c, d, a, b, x[i + 3], 16, -722521979);
    b = md5hh(b, c, d, a, x[i + 6], 23, 76029189);

    a = md5hh(a, b, c, d, x[i + 9], 4, -640364487);
    d = md5hh(d, a, b, c, x[i + 12], 11, -421815835);
    c = md5hh(c, d, a, b, x[i + 15], 16, 530742520);
    b = md5hh(b, c, d, a, x[i + 2], 23, -995338651);

    return [a, b, c, d];
};

var fourthChunk = function fourthChunk(chunks, x, i) {
    var _chunks4 = (0, _slicedToArray3["default"])(chunks, 4),
        a = _chunks4[0],
        b = _chunks4[1],
        c = _chunks4[2],
        d = _chunks4[3];

    a = md5ii(a, b, c, d, x[i], 6, -198630844);
    d = md5ii(d, a, b, c, x[i + 7], 10, 1126891415);
    c = md5ii(c, d, a, b, x[i + 14], 15, -1416354905);
    b = md5ii(b, c, d, a, x[i + 5], 21, -57434055);

    a = md5ii(a, b, c, d, x[i + 12], 6, 1700485571);
    d = md5ii(d, a, b, c, x[i + 3], 10, -1894986606);
    c = md5ii(c, d, a, b, x[i + 10], 15, -1051523);
    b = md5ii(b, c, d, a, x[i + 1], 21, -2054922799);

    a = md5ii(a, b, c, d, x[i + 8], 6, 1873313359);
    d = md5ii(d, a, b, c, x[i + 15], 10, -30611744);
    c = md5ii(c, d, a, b, x[i + 6], 15, -1560198380);
    b = md5ii(b, c, d, a, x[i + 13], 21, 1309151649);

    a = md5ii(a, b, c, d, x[i + 4], 6, -145523070);
    d = md5ii(d, a, b, c, x[i + 11], 10, -1120210379);
    c = md5ii(c, d, a, b, x[i + 2], 15, 718787259);
    b = md5ii(b, c, d, a, x[i + 9], 21, -343485551);
    return [a, b, c, d];
};
/*
 * Calculate the MD5 of an array of little-endian words, and a bit length.
 */
var binlMD5 = function binlMD5(x, len) {
    /* append padding */
    x[len >> 5] |= 0x80 << len % 32;
    x[(len + 64 >>> 9 << 4) + 14] = len;
    var commands = [firstChunk, secondChunk, thirdChunk, fourthChunk];
    var initialChunks = [1732584193, -271733879, -1732584194, 271733878];
    return (0, _from2["default"])({
        length: Math.floor(x.length / 16) + 1
    }, function (v, i) {
        return i * 16;
    }).reduce(function (chunks, i) {
        return commands.reduce(function (newChunks, apply) {
            return apply(newChunks, x, i);
        }, chunks.slice()).map(function (chunk, index) {
            return safeAdd(chunk, chunks[index]);
        });
    }, initialChunks);
};

/*
 * Convert an array of little-endian words to a string
 */
var binl2rstr = function binl2rstr(input) {
    return Array(input.length * 4).fill(8).reduce(function (output, k, i) {
        return output + String.fromCharCode(input[i * k >> 5] >>> i * k % 32 & 0xFF);
    }, '');
};

/*
 * Convert a raw string to an array of little-endian words
 * Characters >255 have their high-byte silently ignored.
 */
var rstr2binl = function rstr2binl(input) {
    return (0, _from2["default"])(input).map(function (i) {
        return i.charCodeAt(0);
    }).reduce(function (output, cc, i) {
        var resp = output.slice();
        resp[i * 8 >> 5] |= (cc & 0xFF) << i * 8 % 32;
        return resp;
    }, []);
};

/*
 * Calculate the MD5 of a raw string
 */
var rstrMD5 = function rstrMD5(string) {
    return binl2rstr(binlMD5(rstr2binl(string), string.length * 8));
};
/*
 * Calculate the HMAC-MD5, of a key and some data (raw strings)
 */
var strHMACMD5 = function strHMACMD5(key, data) {
    var bkey = rstr2binl(key),
        ipad = Array(16).fill(undefined ^ 0x36363636),
        opad = Array(16).fill(undefined ^ 0x5C5C5C5C);

    if (bkey.length > 16) {
        bkey = binlMD5(bkey, key.length * 8);
    }

    bkey.forEach(function (k, i) {
        ipad[i] = k ^ 0x36363636;
        opad[i] = k ^ 0x5C5C5C5C;
    });

    return binl2rstr(binlMD5(opad.concat(binlMD5(ipad.concat(rstr2binl(data)), 512 + data.length * 8)), 512 + 128));
};

/*
 * Convert a raw string to a hex string
 */
var rstr2hex = function rstr2hex(input) {
    var hexTab = function hexTab(pos) {
        return '0123456789abcdef'.charAt(pos);
    };
    return (0, _from2["default"])(input).map(function (c) {
        return c.charCodeAt(0);
    }).reduce(function (output, x, _i) {
        return output + hexTab(x >>> 4 & 0x0F) + hexTab(x & 0x0F);
    }, '');
};

/*
 * Encode a string as utf-8
 */

var str2rstrUTF8 = function str2rstrUTF8(unicodeString) {
    if (typeof unicodeString !== 'string') throw new TypeError('parameter ‘unicodeString’ is not a string');
    var cc = function cc(c) {
        return c.charCodeAt(0);
    };
    return unicodeString.replace(/[\u0080-\u07ff]/g, // U+0080 - U+07FF => 2 bytes 110yyyyy, 10zzzzzz
    function (c) {
        return String.fromCharCode(0xc0 | cc(c) >> 6, 0x80 | cc(c) & 0x3f);
    }).replace(/[\u0800-\uffff]/g, // U+0800 - U+FFFF => 3 bytes 1110xxxx, 10yyyyyy, 10zzzzzz
    function (c) {
        return String.fromCharCode(0xe0 | cc(c) >> 12, 0x80 | cc(c) >> 6 & 0x3F, 0x80 | cc(c) & 0x3f);
    });
};

/*
 * Take string arguments and return either raw or hex encoded strings
 */
var rawMD5 = function rawMD5(s) {
    return rstrMD5(str2rstrUTF8(s));
};

var hexMD5 = function hexMD5(s) {
    return rstr2hex(rawMD5(s));
};

var rawHMACMD5 = function rawHMACMD5(k, d) {
    return strHMACMD5(str2rstrUTF8(k), str2rstrUTF8(d));
};

var hexHMACMD5 = function hexHMACMD5(k, d) {
    return rstr2hex(rawHMACMD5(k, d));
};

exports["default"] = function (string, key, raw) {
    if (!key) {
        if (!raw) {
            return hexMD5(string);
        }
        return rawMD5(string);
    }
    if (!raw) {
        return hexHMACMD5(key, string);
    }
    return rawHMACMD5(key, string);
};

/***/ })
/******/ ]);
//# sourceMappingURL=p13n.js.map
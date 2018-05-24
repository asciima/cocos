    /**
    * cc.sys.localStorage is a local storage component.
    */
    
    window.UserDefault = {};

    /**
    * @param {string} _key
    * @param {boolean} _value
    */
    UserDefault.setBool = function (_key, _value) {
        cc.sys.localStorage.setItem(_key, _value.toString());
    };

    /**
    * @param {string} _key
    * @param {boolean} _defaultValue
    * @returns {boolean}
    */
    UserDefault.getBool = function (_key, _defaultValue) {
        var value = cc.sys.localStorage.getItem(_key);
        if (value !== null && value.length !== 0) {
            return value === "false" ? false : true;
        } else if (_defaultValue !== undefined) {
            return _defaultValue;
        } else {
            return false;
        }
    };

    /**
    * @param {string} _key
    * @param {number} _value
    */
    UserDefault.setInt = function (_key, _value) {
        cc.sys.localStorage.setItem(_key, _value.toString())
    };

    /**
    * @param {string} _key
    * @param {number} _defaultValue
    * @returns {number}
    */
    UserDefault.getInt = function (_key, _defaultValue) {
        var value = cc.sys.localStorage.getItem(_key);
        if (value !== null && value.length !== 0) {
            return Number(value);
        } else if (_defaultValue !== undefined) {
            return _defaultValue;
        } else {
            return 0;
        }
    };

    /**
    * @param {string} _key
    * @param {string} _value
    */
    UserDefault.setString = function (_key, _value) {
        cc.sys.localStorage.setItem(_key, _value)
    };

    /**
    * @param {string} _key
    * @param {string} _defaultValue
    * @returns {string}
    */
    UserDefault.getString = function (_key, _defaultValue) {
        var value = cc.sys.localStorage.getItem(_key);
        if (value !== null && value.length !== 0) {
            return value;
        } else if (_defaultValue !== undefined) {
            return _defaultValue;
        } else {
            return "";
        }
    };

    /**
    * @param {string} _key
    * @param {object} _value
    */
    UserDefault.setObject = function (_key, _value) {
        cc.sys.localStorage.setItem(_key, JSON.stringify(_value))
    };

    /**
    * @param {string} _key
    * @param {object} _defaultValue
    * @returns {object}
    */
    UserDefault.getObject = function (_key, _defaultValue) {
        var value = cc.sys.localStorage.getItem(_key);
        if (value !== null && value.length !== 0) {
            return JSON.parse(value);
        } else if (_defaultValue !== undefined) {
            return _defaultValue;
        } else {
            return null;
        }
    };
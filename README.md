# grunt-file-modify

> modify file content.

## Getting Started
This plugin requires Grunt `~0.4.5`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-file-modify --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-file-modify');
```

## The "file_modify" task

### Overview
In your project's Gruntfile, add a section named `file_modify` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  file_modify: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
});
```

### Options

#### options.process
Type: `Function(content, srcpath)`

`options.process` �������ݸ� `grunt.file.copy` �����ڿ�����Щ���ݿ��Ա����������棩��**�ú�����Ҫ����һ���µ��ļ�������**��

- `content` �� ���ļ���ԭʼ���ݣ�����ͨ���޸� `content` �Ӷ�����µ��ļ�����
- `srcpath` �� ���ļ��ȶ���Gruntfile.js��·��


### Usage Examples

#### �Զ��巽���޸��ļ�����
������������У����ǽ�ȥ�������� ��//@debug�� ���е����ݡ�Ϊʲô��Ҫ��ô������Ϊ�ܶ�ʱ�������ڵ���ʱ��Ҫ��ӡ�������ݣ������������汾ʱ�����Ǿ���Ҫ�Ƴ���Щ���롣ʹ�õ���ע�������ӡ�//@debug���ı�־�����ܹ�ʹ�������ܹ�����������Щ��������Ҫ�ڷ����汾��ɾ���ġ�

```js
grunt.initConfig({
  file_modify: {
    options: {
        process: function (content, srcpath) {
            /**
             * ȥ�������� ��//@debug�� ���е����ݣ�����������һ����Ϊ������@debug����������ݽ����滻Ϊ�հ�
             * console.log(s1); // @debug remove this line, too!
             */
            return content.replace(/[^\n]+\/\/\s*@\s*debug.*/g, '');
        }
    },
    src: ['tmp/options_process.js']
  },
});
```


## Release History
2015.11.23 v0.1.0 Support `options.process` to modify file content.
2015.11.23 v0.0.1 Init.

# YzyAddUpdate

**自己实现增量更新框架** 


- DiffProject是生成差分包的工程，里面已经编译好了win64下的动态链接库，可以直接拿来在java层调用  

1、建立一个包名为“com.demo.yzy”的包，里面创建一个DiffUtil的类，并写上本地方法

		package com.demo.yzy;
		public class DiffUtil {
			/**
			 * 进行差分的本地方法
			 * @param oldfile 旧版本文件路径
			 * @param newfile 新版本文件路径
			 * @param patchfile	差分后的文件保存路径
			 */
			public native void diff(String oldfile,String newfile,String patchfile);
		}

2、将动态链接库引入项目中，调用本地方法diff()即可得到差分包

- 合并（将旧版本和差分包合并成新apk）待续。。。。。。


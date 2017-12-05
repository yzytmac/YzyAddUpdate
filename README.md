# YzyAddUpdate

**自己实现增量更新差分包与合并** 


1、DiffProjectWin是windows下生成差分包的工程，里面已经编译好了win64下的动态链接库，可以直接拿来在java层调用  

- 建立一个包名为“com.demo.yzy”的包，里面创建一个DiffUtil的类，并写上本地方法

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

- 将动态链接库引入项目中，调用本地方法diff()即可得到差分包

2、src_Linux里面是是Linux（Android）下的差分和合并的代码，可以自己编译


3、其余的arm64-v8a、arm64、arm64-v7a、mips、mips64、x86、x86_64里面是已经编译好的so库文件  
可以直接使用。使用方法如下  

        1、建立一个包“com.yzy.diffandpatchproject”
        2、在该包下建立一个类  
        public class DiffAndPatchUtil {
        	public native static void diff(String oldFile,String newFile,String patchFile);
        	
        	public native static void patch(String oldFile,String newFile,String patchFile);
        
        }  
        3、在使用的地方引入so库  
        static{
            System.loadLibrary("bsdiff");
            System.loadLibrary("bspatch");
        }
        4、使用差分和合并方法
        DiffAndPatchUtil.diff(oldFile, newFile, patchFile);//差分
        DiffAndPatchUtil.patch(oldFile, newFile, patchFile);//合并
        

        


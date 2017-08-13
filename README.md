/*# BinaryToLetter
二进制 转 英语字母*/

import java.util.*;
public class BinaryToLetter {

	public static void main(String[] args) {
		Scanner s=new Scanner(System.in);
		System.out.println("请输入二进制数");
		String ejz=s.nextLine();
		int n=ejz.length();
		ejz=strComplete(ejz,n);
		n=ejz.length();
		int i=n/7;
		String result[]=new String[i];//储存调用strIntercept函数的值
		for(int a=0;a<i;a++){
			result[a]=strIntercept(a,ejz);
		}
		int sjz[]=new int[i];
		for(int b=0;b<i;b++){
			sjz[b]=ejzCount(result[b]);
		}
		char English[]=new char[i];
		for(int c=0;c<i;c++){
			English[c]=(char)sjz[c];
			System.out.print(English[c]);
		}





	}
	static String strComplete(String ejz,int n){//补齐二进制数
		int a=7-n%7;
		if(a!=7){
			for(int b=0;b<a;b++){
				ejz="0"+ejz;
			}
		}
		return ejz;
	}
	/*strIntercept截取函数将String类型的二进制以7个为准分组*/
	static String strIntercept(int a,String ejz){
		String str="";
		for(int b=a*7;b<a*7+7;b++){
			str=str+ejz.charAt(b);
		}
		return str;
	}
	/*ejzCount函数计算并将以String类型显示的二进制数以int型转化为十进制*/
	static int ejzCount(String result){
		int sjz=0;
		int intejz_1[]=new int[7];		
		String strejz[]=new String[7];
		for(int a=0;a<7;a++){
			intejz_1[a]=1;
		}
		for(int b=0;b<7;b++){
			strejz[b]=String.valueOf(result.charAt(b));
		}
		for(int c=0;c<7;c++){
			if(strejz[c].equals("1")){
				for(int d=0;d<6-c;d++){
					intejz_1[c]*=2;
				}
			}else{
				intejz_1[c]=0;
			}
		}
		for(int e=0;e<7;e++){
			sjz=sjz+intejz_1[e];
		}
		return sjz;
	}
	
}

# Chapter9Problem
public class StopWatch {
	private long startTime;
	private long endTime;
	
	public StopWatch(){
		startTime=System.currentTimeMillis();
	}
	
	public void start() {
		startTime=System.currentTimeMillis();
	}
	
	public void stop() {
		endTime=System.currentTimeMillis();
	}
	
	public long getElapsedTime() {
		return endTime - startTime;
	}
}

public class Test {

	public static void main(String[] args) {
		final int lengthOfArray=100000;
		//测试选择排序算法执行时间
		StopWatch date=new StopWatch();
		int[]randomArray=new int[lengthOfArray];
		for(int i=0;i<lengthOfArray;++i) {
			randomArray[i]=(int)(Math.random()*lengthOfArray);
		}
		date.start();
		for(int i=0;i<lengthOfArray-1;++i) {
			int min=randomArray[i];
			int minPosition=i;
			for(int j=i+1;j<lengthOfArray;++j) {
				if(min>randomArray[j]) {
					min=randomArray[j];
					minPosition=j;
				}
			}
			if(i!=minPosition) {
				int temp=randomArray[i];
				randomArray[i]=randomArray[minPosition];
				randomArray[minPosition]=temp;
			}
		}
		date.stop();
		System.out.print(date.getElapsedTime());
	}

}

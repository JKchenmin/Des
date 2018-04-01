# Des
DES加密算法

import java.util.Scanner;

public class Des {

    static int ip[] = {58,50,42,34,26,18,10,2,
                        60,52,44,36,28,20,12,4,
                        62,54,46,38,30,22,14,6,
                        64,56,48,40,32,24,16,8,
                        57,49,41,33,25,17,9,1,
                        59,51,43,35,27,19,11,3,
                        61,53,45,37,29,21,13,5,
                        63,55,47,39,31,23,15,7};

    static int ip1[] = {40,8,48,16,56,24,64,32,
                        39,7,47,15,55,23,63,31,
                        38,6,46,14,54,22,62,30,
                        37,5,45,13,53,21,61,29,
                        36,4,44,12,52,20,60,28,
                        35,3,43,11,51,19,59,27,
                        34,2,42,10,50,18,58,26,
                        33,1,41,9,49,17,57,25};


    //将数据扩展为64位bit
    public static String getBit(int n){
        //构造64个"0"
        StringBuffer stringBuffer = new StringBuffer();
        for (int i = 0; i < 64; i++) {
            stringBuffer.append("0");
        }
        //将十进制参数转化为二进制
        String binary = Integer.toBinaryString(n);
        //将二进制的数长度扩展为64为
        binary = stringBuffer.substring(0, 64 - binary.length()) + binary;
        return binary;
    }

    //进行初始置换
    public static StringBuffer IPChange(String m){
        StringBuffer dst = new StringBuffer();
        for (int i = 0; i < m.length(); i++) {
            dst.append(m.charAt(ip[i]-1));

        }
        return dst;
    }

    //进行初始逆置换
    public static StringBuffer IP1Change(String m){
        StringBuffer dst = new StringBuffer();
        for (int i = 0; i < m.length(); i++) {
            dst.append(m.charAt(ip1[i]-1));
        }
        return dst;
    }

    public static void main(String[] args) {
        int m = 0;
        System.out.println("请输入一个明文：");
        Scanner input = new Scanner(System.in);
        m = input.nextInt();
        String binary = getBit(m);
        System.out.println("开始执行");
        StringBuffer IPSb = IPChange(binary);
        StringBuffer IP1Sb = IP1Change(IPSb.toString());
        System.out.println("初始置换后的值为:"+IPSb.toString());
        System.out.println("初始逆置换后的值为:"+IP1Sb.toString());
    }

}

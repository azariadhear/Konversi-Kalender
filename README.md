# Konversi-Kalender
package KonversiKalender;

/**
 * @author Azaria Dhea Rismaya
 */
import java.util.Scanner;

public class Konversi_kalender {

    public static void main(String[] args) {
        for (String ulang = "y"; ulang.equals("y") || ulang.equals("Y");){
        String mbulan[]={"Januari","Februari","Maret","April","Mei","Juni",
            "Juli","Agustus","September","Oktober","November","Desember"};
        String hbulan[]={"Muharam","Safar","Rabiulawal","Rabiulakhir",
            "Jumadilawal","Jumadilakhir","Rajab","Syakban","Ramadan","Syawal",
            "Zulkaidah","Zulhijah"};
        Scanner input = new Scanner (System.in);
        do {
            int a, b, c, d, e, f, pilih, hari, bulan, tahun, tgl, bln, thn;
            System.out.println("KONVERSI TANGGAL MASEHI/HIJRIAH");
            System.out.println("1. Dari Masehi ke Hijriah");
            System.out.println("2. Dari Hijriah ke Masehi");
            System.out.println("Masukkan Pilihan Anda: ");
            pilih=input.nextInt();
            switch(pilih){
                
                case 1:
                    System.out.println("Input tanggal Masehi : ");
                    tgl=input.nextInt();
                    System.out.println("Input bulan Masehi (dalam angka) : ");
                    bln=input.nextInt();
                    System.out.println("Input tahun Masehi : ");
                    thn=input.nextInt();
                    if(bln==2 && tgl>=29 && thn%4!=0){
                        System.out.println("Tanggal yang Anda masukkan salah");
                        break;}
                    else
                        System.out.println("Tanggal yang Anda masukkan: "+tgl
                                +" "+mbulan[bln-1]+" "+thn);
                    
                    if ((thn > 1582) || ((thn == 1582) && (bln > 10)) || 
                            ((thn == 1582) && (bln == 10) && (tgl > 14))) {
                        a=((1461 * (thn + 4800 + ((bln - 14) / 12))) / 4) 
                                + ((367 * (bln - 2 - 12 * (((bln - 14) / 12)))) 
                                / 12) - ((3 * (((thn + 4900 + ((bln - 14) / 12)) 
                                / 100)))/ 4) + tgl - 32075;
                    } else {
                        a= 367 * thn - ((7 * (thn + 5001 + ((bln - 9) / 7))) 
                                / 4) + ((275 * bln) / 9) + tgl + 1729777;
                    }
                    b=a - 1948440 + 10632;
                    c=((b - 1) / 10631);
                    b=b - 10631 * c + 354;
                    d=(((10985 - b) / 5316)) * (((50 * b) / 17719)) 
                            + ((b / 5670)) *(((43 * b) / 15238));
                    b=b-(((30 - d) / 15)) * (((17719 * d) / 50))-((d / 16)) 
                            * (((15238 * d) / 43)) + 29;
                    bulan=((24 * b) / 709);
                    hari=b-((709 * bulan) / 24);
                    tahun=30 * c + d - 30;
                    System.out.println("Konversi ke Hijriah menjadi: "+hari
                            +" "+hbulan[bulan-1]+" "+tahun);
                    break;
                
                case 2:
                    System.out.println("Input tanggal Hijriah : ");
                    tgl=input.nextInt();
                    System.out.println("Input bulan Hijriah (dalam angka) : ");
                    bln=input.nextInt();
                    
                    System.out.println("Input tahun Hijriah : ");
                    thn=input.nextInt();
                    System.out.println("Tanggal yang Anda masukkan: "+tgl
                            +" "+hbulan[bln-1]+" "+thn);
                    a = ((11*thn+3)/30)+354*thn+30*bln-((bln-1)/2)+tgl+1948440
                            -385;
                    if (a>2299160){
                        b=a+68569;
                        c=((4*b)/146097);
                        b=b-((146097*c+3)/4);
                        e=((4000*(b+1))/1461001);
                        b=b-((1461*e)/4)+31;
                        d=((80*b)/2447);
                        hari=b-((2447*d)/80);
                        b=(d/11);
                        bulan=d+2-12*b;
                        tahun=100*(c-49)+e+b;
                    }else{
                        d=a+1402;
                        f=((d-1)/1461);
                        b=d-1461*f;
                        c=((b-1)/365)-(b/1461);
                        e=b-365*c+30;
                        d=((80*e)/2447);
                        hari=e-((2447*d)/80);
                        e=(d/11);
                        bulan=d+2-12*e;
                        tahun=4*f+c+e-4716;
                    }
                    System.out.println("Konversi ke Masehi menjadi: "+hari
                            +" "+mbulan[bulan-1]+" "+tahun);
                    break;
                default:
                    System.out.println("Maaf pilihan Anda salah");
                    break;
            }
            System.out.println("Apakah ingin memasukkan tanggal?(y/t)");
            ulang=input.next();
            if (ulang.equals("y")){
                System.out.println("Anda memilih menghitung lagi");
            } else System.out.println("Anda memilih untuk menghentikan program");
        } while(ulang.equals("y"));
        }
    }
}

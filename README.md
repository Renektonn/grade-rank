# grade-//excel成績

import java.util.Scanner;

class Student{
  //int num;
  int Chinese;
  int Math;
  int English;
  double average;
  int rank;
  int group;
  
  public Student(int Chinese , int Math , int English){
    this.Chinese = Chinese;
    this.Math = Math;
    this.English = English;
    this.average = (Chinese + Math + English)/3.0; 
  }

}

class Main {
  static void computeRank(Student [] stu , int num){//error
    int [] rank = new int [stu.length];
    for(int i=1 ; i<=num ; i++){ //init
      rank[i] = i;
    }

    for(int i=1 ; i<=num-1 ; i++){
      for(int j=1 ; j<=num ; j++){
        if(stu[i].average < stu[j].average){
          int tem = rank[i];
          rank[i] = rank[j];
          rank[j] = tem;
        }
      }
    }

    for(int i=1 ; i<=num ; i++){
      stu[ rank[i] ].rank=i;
    }
  }
  
  static void output(Student [] Stu , int num){
    
    System.out.printf("%-10s","num");
    System.out.printf("%-10s","Chinese");
    System.out.printf("%-10s","Math");
    System.out.printf("%-10s","English");
    System.out.printf("%-10s","average");
    System.out.printf("%-10s","rank");
    System.out.println();

    
    for(int i = 1;i <= num;i++){
      System.out.printf("%10d",i);
      System.out.printf("%10d",Stu[i].Chinese);
      System.out.printf("%10d",Stu[i].Math);
      System.out.printf("%10d",Stu[i].English);
      System.out.printf("%10.2f",Stu[i].average);
      System.out.printf("%10.2f",Stu[i].rank);
      System.out.println();
    }
  }

  static void input(Student [] Stu , int num){
    
    Scanner cin = new Scanner (System.in);
    for(int i = 1;i <= num;i++){
      int Chinese = cin.nextInt();
      int Math    = cin.nextInt();
      int English = cin.nextInt();
      Stu[i] = new Student(Chinese , Math , English);
    }
  }

  public static void main(String[] args) {
    
    
    Student [] numStu = new Student [10+1];
    input(numStu,10);
    //numstu;
    computeRank(numStu,10);
    output(numStu,10);
    

    
  }

}


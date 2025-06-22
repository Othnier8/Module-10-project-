# Module-10-project-


using System;
using System.Collections.Generic;

class ContractorModule10 {
   
  static void Main() {
    Console.WriteLine("Hello World");
  }
}
//----
public class Contractor{
    public string ContractorName{get; set;}
    public int ContractorNumber{get; set;}
    public DateTime ContractorStartDate{get; set;}
   
    public Contractor(string name, int number, DateTime startdate)
    {
        ContractorName = name;
        ContractorNumber = number;
        ContractorStartDate = startdate;
    }
    public override string ToString()
    {
        return $"Name: {ContractorName}\nNumber:{ContractorNumber}\nStart Date: { ContractorStartDate}\n";
    }
}
public class Subcontractor: Contractor{
    public int Shift{get; set;}
    public double HourlyPayRate{get; set;}
    public Subcontractor(string name, int number, DateTime startdate,int shift, double payrate)
        :base(name,number,startdate)
    {
        Shift = shift;
        HourlyPayRate = payrate;
    }
   
    public double ComputePay(double hoursworked)
    {
        double pay = (double)(HourlyPayRate*hoursworked);
        if (Shift ==2)
        {
            pay = pay*1.03;
        }
        return pay;
    }
    public override string ToString()
    {
        string shiftname = Shift == 1 ? "Day" :"Night";
        return base.ToString()+ $"\nShift: {shiftname}\nHourly Pay Rate: {HourlyPayRate:C}";
    }

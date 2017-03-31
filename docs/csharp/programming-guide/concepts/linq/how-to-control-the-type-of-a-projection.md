---
title: "方法: プロジェクションの型を制御する (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 465a04338de0a092bf60e15ce07a9aace160bbe3
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-control-the-type-of-a-projection-c"></a>方法: プロジェクションの型を制御する (C#)
射影は、1 つのデータのセットを取得し、フィルター処理し、その形式を変更し、その型も変更するプロセスです。 ほとんどのクエリ式は射影を実行します。 このセクション内のクエリ式は、ほとんどが <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> に評価されますが、プロジェクションの型を制御して別の型のコレクションを作成することができます。 このトピックでは、その方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、`Customer` という新しい型を定義します。 次に、クエリ式の `Customer` 句で新しい `Select` オブジェクトをインスタンス化します。 これによって、クエリ式の型が `Customer` の <xref:System.Collections.Generic.IEnumerable%601> になります。  
  
 この例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)」の XML ドキュメントを使用します。  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return String.Format("{0}:{1}:{2}", this.customerID, this.companyName, this.contactName);  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable.Select%2A>   
 [プロジェクションと変換 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

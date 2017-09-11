---
title: "ジェネリック コレクションに対するインターフェイスでの分散の使用 (C#)"
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
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5d505b566fe604afdedea583dc8c001f80c15d3c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="de9ad-102">ジェネリック コレクションに対するインターフェイスでの分散の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="de9ad-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="de9ad-103">共変のインターフェイスのメソッドでは、そのインターフェイスで指定された型よりも強い派生型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="de9ad-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="de9ad-104">反変のインターフェイスのメソッドでは、そのインターフェイスで指定された型よりも弱い派生型のパラメーターを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="de9ad-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="de9ad-105">.NET Framework 4 では、既存のいくつかのインターフェイスが共変および反変になります。</span><span class="sxs-lookup"><span data-stu-id="de9ad-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="de9ad-106">その中には、<xref:System.Collections.Generic.IEnumerable%601> や <xref:System.IComparable%601> があります。</span><span class="sxs-lookup"><span data-stu-id="de9ad-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="de9ad-107">これにより、派生型のコレクションに対して、基本型のジェネリック コレクションを操作するメソッドを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="de9ad-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="de9ad-108">.NET Framework のバリアント インターフェイスの一覧については、「[Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)」 (ジェネリック インターフェイスの分散 (C#)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de9ad-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="de9ad-109">ジェネリック コレクションの変換</span><span class="sxs-lookup"><span data-stu-id="de9ad-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="de9ad-110">次の例は、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにおける共変性のサポートの利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="de9ad-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="de9ad-111">`PrintFullName` メソッドは、パラメーターとして `IEnumerable<Person>` 型のコレクションを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="de9ad-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="de9ad-112">ただし、`Employee` は `Person` を継承しているため、`IEnumerable<Employee>` 型のコレクションで再利用できます。</span><span class="sxs-lookup"><span data-stu-id="de9ad-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="de9ad-113">ジェネリック コレクションの比較</span><span class="sxs-lookup"><span data-stu-id="de9ad-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="de9ad-114">次の例は、<xref:System.Collections.Generic.IComparer%601> インターフェイスにおける反変性のサポートの利点を示しています。</span><span class="sxs-lookup"><span data-stu-id="de9ad-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="de9ad-115">`PersonComparer` クラスは、`IComparer<Person>` インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="de9ad-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="de9ad-116">ただし、`Employee` は `Person` を継承しているため、`Employee` 型の一連のオブジェクトを比較するためにこのクラスを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="de9ad-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="de9ad-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="de9ad-117">See Also</span></span>  
 [<span data-ttu-id="de9ad-118">ジェネリック インターフェイスの分散 (C#)</span><span class="sxs-lookup"><span data-stu-id="de9ad-118">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)


---
title: "方法: 自動実装するプロパティを使用して簡易クラスを実装する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2b944b6d232925bbd9bf1c04e89cd40e5ceaf016
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="e6758-102">方法: 自動実装するプロパティを使用して簡易クラスを実装する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e6758-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="e6758-103">この例では、一連の自動実装プロパティのカプセル化のみを行う、変更できない簡易クラスの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e6758-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="e6758-104">参照型のセマンティクスを使用する必要がある場合は、構造体ではなく次のようなコンストラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6758-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>  
  
 <span data-ttu-id="e6758-105">変更できないプロパティの作成方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="e6758-105">You can make an immutable property in two ways.</span></span>  <span data-ttu-id="e6758-106">[set](../../../csharp/language-reference/keywords/set.md) アクセサーは、[private](../../../csharp/language-reference/keywords/private.md) として宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="e6758-106">You can declare the [set](../../../csharp/language-reference/keywords/set.md) accessor.to be [private](../../../csharp/language-reference/keywords/private.md).</span></span>  <span data-ttu-id="e6758-107">プロパティは型の中のみで設定可能で、コンシューマーは変更できません。</span><span class="sxs-lookup"><span data-stu-id="e6758-107">The property is only settable within the type, but it is immutable to consumers.</span></span>  <span data-ttu-id="e6758-108">代わりに [get](../../../csharp/language-reference/keywords/get.md) アクセサーのみを宣言し、型のコンストラクターを除くすべての場所でプロパティを変更できないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e6758-108">You can instead declare only the [get](../../../csharp/language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>  
  
 <span data-ttu-id="e6758-109">`set` アクセサーを private で宣言した場合、オブジェクト初期化子を使用してプロパティを初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="e6758-109">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="e6758-110">コンストラクターまたはファクトリ メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6758-110">You must use a constructor or a factory method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6758-111">例</span><span class="sxs-lookup"><span data-stu-id="e6758-111">Example</span></span>  
 <span data-ttu-id="e6758-112">次の例は、自動実装プロパティを持つ変更できないクラスを実装する 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e6758-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="e6758-113">それぞれの方法では、プロパティの 1 つを private `set` で、1 つを `get` のみで宣言します。</span><span class="sxs-lookup"><span data-stu-id="e6758-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="e6758-114">最初のクラスはプロパティの初期化にコンストラクターのみを使用しますが、2 番目のクラスは、コンストラクターを呼び出す静的ファクトリ メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e6758-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>  
  
```csharp  
// This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // constructor to initialize its properties.   
    class Contact  
    {  
        // Read-only properties.   
        public string Name { get; }  
        public string Address { get; private set; }  
  
        // Public constructor.   
        public Contact(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
    }  
  
    // This class is immutable. After an object is created,   
    // it cannot be modified from outside the class. It uses a   
    // static method and private constructor to initialize its properties.      
    public class Contact2  
    {  
        // Read-only properties.   
        public string Name { get; private set; }  
        public string Address { get; }  
  
        // Private constructor.   
        private Contact2(string contactName, string contactAddress)  
        {  
            Name = contactName;  
            Address = contactAddress;                 
        }  
  
        // Public factory method.   
        public static Contact2 CreateContact(string name, string address)  
        {  
            return new Contact2(name, address);  
        }  
    }  
  
    public class Program  
    {   
        static void Main()  
        {  
            // Some simple data sources.   
            string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",   
                              "Cesar Garcia", "Debra Garcia"};  
            string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",  
                                  "12 108th St.", "89 E. 42nd St."};  
  
            // Simple query to demonstrate object creation in select clause.   
            // Create Contact objects by using a constructor.   
            var query1 = from i in Enumerable.Range(0, 5)  
                        select new Contact(names[i], addresses[i]);  
  
            // List elements cannot be modified by client code.   
            var list = query1.ToList();  
            foreach (var contact in list)  
            {  
                Console.WriteLine("{0}, {1}", contact.Name, contact.Address);  
            }  
  
            // Create Contact2 objects by using a static factory method.   
            var query2 = from i in Enumerable.Range(0, 5)  
                         select Contact2.CreateContact(names[i], addresses[i]);  
  
            // Console output is identical to query1.   
            var list2 = query2.ToList();  
  
            // List elements cannot be modified by client code.   
            // CS0272:   
            // list2[0].Name = "Eugene Zabokritski";   
  
            // Keep the console open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();                  
        }  
    }  
  
/* Output:  
    Terry Adams, 123 Main St.  
    Fadi Fakhouri, 345 Cypress Ave.  
    Hanying Feng, 678 1st Ave  
    Cesar Garcia, 12 108th St.  
    Debra Garcia, 89 E. 42nd St.  
*/  
```  
  
 <span data-ttu-id="e6758-115">コンパイラによって、各自動実装プロパティにバッキング フィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e6758-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="e6758-116">このフィールドは、ソース コードから直接アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="e6758-116">The fields are not accessible directly from source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6758-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6758-117">See Also</span></span>  
 <span data-ttu-id="e6758-118">[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="e6758-118">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="e6758-119">[struct](../../../csharp/language-reference/keywords/struct.md) </span><span class="sxs-lookup"><span data-stu-id="e6758-119">[struct](../../../csharp/language-reference/keywords/struct.md) </span></span>  
 [<span data-ttu-id="e6758-120">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="e6758-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)


---
title: "using ディレクティブ (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e91cc4fea9fbe57b257e17915cd28b3b82f12f6e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="using-directive-c-reference"></a>using ディレクティブ (C# リファレンス)
`using` ディレクティブは、次の 3 つの用途で使用します。  
  
-   名前空間で型の使用を許可する場合。これにより、その名前空間内では型を修飾せずに使用できます。  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   アクセスを型名で修飾することなく、型の静的メンバーへのアクセスを許可する場合。 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    詳細については、「[using static ディレクティブ](using-static.md)」を参照してください。

-   名前空間または型のエイリアスを作成する場合。 これは "*using エイリアス ディレクティブ*" と呼ばれます。  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` キーワードは、"*using ステートメント*" の作成にも使用されます。このキーワードによって、ファイル、フォントなどの <xref:System.IDisposable> オブジェクトが正しく処理されます。 詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。  
  
## <a name="using-static-type"></a>using static 型  
 アクセスを型名で修飾することなく型の静的メンバーにアクセスできます。  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a>コメント  
 `using` ディレクティブのスコープは、このディレクティブが存在するファイルに限定されます。  
  
 `using` エイリアスを作成すると、名前空間または型への識別子を修飾しやすくなります。 using エイリアス ディレクティブの右側は、その前にある using ディレクティブに関係なく、必ず完全修飾型である必要があります。  
  
 `using` ディレクティブを作成すると、名前空間内の型を、名前空間を指定することなく使用できます。 `using` ディレクティブでは、指定した名前空間に入れ子になった別の名前空間へのアクセスは許可されません。  
  
 名前空間は、ユーザー定義とシステム定義の 2 つのカテゴリに分類されます。 ユーザー定義の名前空間は、コードで定義された名前空間です。 システム定義の名前空間の一覧については、「[.NET Framework クラス ライブラリ](http://go.microsoft.com/fwlink/?LinkID=227195)」を参照してください。  
  
 他のアセンブリのメソッドを参照する方法の例については、[C# DLL の作成と使用](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)に関するページをご覧ください。  
  
## <a name="example-1"></a>例 1  
  
 次の例は、名前空間の `using` エイリアスを定義して使用する方法を示しています。  
  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 using エイリアス ディレクティブの右側には、オープン ジェネリック型を配置できません。 たとえば、List\<T> の using エイリアスを作成することはできませんが、List\<int> の using エイリアスは作成できます。  
  
## <a name="example-2"></a>例 2  
  
 次の例は、クラスの `using` ディレクティブと `using` エイリアスを定義する方法を示しています。  
  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)   
 [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)


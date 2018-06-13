---
title: using ディレクティブ (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280092"
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
  
 `using` キーワードは、*using ステートメント*の作成にも使用します。ファイルやフォントなどの <xref:System.IDisposable> オブジェクトを正しく処理できるようになります。 詳しくは、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」をご覧ください。  
  
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
  
 名前空間は、ユーザー定義とシステム定義の 2 つのカテゴリに分類されます。 ユーザー定義の名前空間は、コードで定義された名前空間です。 システム定義の名前空間の一覧については、[.NET Framework クラス ライブラリの概要](../../../standard/class-library-overview.md)に関するページを参照してください。  
  
 他のアセンブリのメソッドを参照する方法の例については、[コマンド ラインでアセンブリを作成し、使用する](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)方法に関するページをご覧ください。  
  
## <a name="example-1"></a>例 1  
  
 次の例は、名前空間の `using` エイリアスを定義して使用する方法を示しています。  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 using エイリアス ディレクティブの右側には、オープン ジェネリック型を配置できません。 たとえば、List\<T> の using エイリアスを作成することはできませんが、List\<int> の using エイリアスは作成できます。  
  
## <a name="example-2"></a>例 2  
  
 次の例は、クラスの `using` ディレクティブと `using` エイリアスを定義する方法を示しています。  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)  
 [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)

---
title: '#line (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: 08ba94ec3f1799f858e098bd2c0e059b7f45af2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="line-c-reference"></a>#line (C# リファレンス)
`#line` を使用すると、コンパイラの行番号および (必要に応じて) エラーと警告に出力されるファイル名を変更することができます。 この例では、行番号に関連付けられている 2 つの警告を報告する方法を示します。 `#line 200` ディレクティブは行番号が 200 (既定では 7) になるように強制し、次の #line ディレクティブまでファイル名を "Special" として報告します。 #line default ディレクティブは、行の番号付けをその既定の番号付けに戻します。つまり、前のディレクティブで番号が付け直された行をカウントします。  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a>コメント  
 `#line` ディレクティブは、ビルド プロセスで自動化された中間ステップで使用される場合があります。 たとえば、行が元のソース コード ファイルから削除されても、ファイル内の元の行番号付けに基づいてコンパイラに引き続き出力を生成させる場合は、行を削除してから `#line` を使用して元の行番号付けをシミュレートできます。  
  
 開発者がコードをステップ実行すると、`#line hidden` と次の `#line` ディレクティブ (別の `#line hidden` ディレクティブではないと仮定) の間のすべての行がステップ オーバーされるように、`#line hidden` ディレクティブは、連続する行をデバッガーから隠します。 このオプションは、ユーザー定義のコードとコンピューターによって生成されたコードを ASP.NET が区別できるようするために使用することもできます。 この機能を主に使用しているのは ASP.NET ですが、より多くのソース ジェネレーターが利用できる可能性はあります。  
  
 `#line hidden` ディレクティブはエラーの報告でのファイル名や行番号には影響しません。 つまり、非表示のブロックでエラーが発生した場合、コンパイラはエラーの現在のファイル名と行番号を報告します。  
  
 `#line filename` ディレクティブは、コンパイラ出力に表示するファイル名を指定します。 既定では、ソース コード ファイルの実際の名前が使用されます。 ファイル名は、二重引用符 ("") で囲み、前に行番号を付ける必要があります。  
  
 ソース コード ファイルは、任意の数の `#line` ディレクティブを持つことができます。  
  
## <a name="example-1"></a>例 1  
 次の例では、デバッガーがコード内の非表示の行を無視する方法を示します。 例を実行すると、次の 3 行のテキストが表示されます。 しかし、例に示されているようにブレークポイントを設定し、F10 キーを押してコードをステップ実行すると、デバッガーが非表示の行を無視することがわかります。 非表示の行にブレークポイントを設定した場合でも、デバッガーは無視することに注目してください。  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)

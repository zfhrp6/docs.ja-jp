---
title: "/define (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/define"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-define compiler option [C#]"
  - "/define compiler option [C#]"
  - "-d compiler option [C#]"
  - "define compiler option [C#]"
  - "/d compiler option [C#]"
  - "d compiler option [C#]"
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /define (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/define** オプションは、`name` をプログラムのすべてのソース コード ファイル内のシンボルとして定義します。  
  
## 構文  
  
```  
/define:name[;name2]  
```  
  
## Arguments  
 `name`, `name2`  
 定義する 1 つ以上の記号の名前。  
  
## 解説  
 **\/define** オプションには、[\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) プリプロセッサ ディレクティブを使用する場合と同じ効果があります。ただし、コンパイラ オプションがプロジェクト内のすべてのファイルに対して有効な点が異なります。  ソース ファイルの [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) ディレクティブがこの定義を削除するまで、ソース ファイルのシンボルは削除されません。  \/define オプションを使用する場合、あるファイルで指定されている `#undef` ディレクティブは、プロジェクト内の他のソース コード ファイルには影響しません。  
  
 このオプションで作成されるシンボルを [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)、[\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、および [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) で使用すると、ソース ファイルを条件付きでコンパイルできます。  
  
 **\/d** は **\/define** の省略形です。  
  
 **\/define** では、シンボル名をセミコロンまたはコンマで区切ることにより、複数のシンボルを定義できます。  たとえば、次のようになります。  
  
```  
/define:DEBUG;TUESDAY  
```  
  
 C\# コンパイラ自体は、ソース コードで使用できるシンボルやマクロを定義しません。すべてのシンボル定義はユーザーが定義する必要があります。  
  
> [!NOTE]
>  C\+\+ などの言語とは異なり、C\# の `#define` では、シンボルに値を割り当てることはできません。  たとえば、マクロの作成や定数の定義に `#define` を使用することはできません。  定数を定義する必要がある場合は、`enum` 変数を使用します。  C\+\+ のようなマクロを作成する場合は、ジェネリックなどで代用してください。  マクロはエラーを招きやすいため、C\# では、マクロの使用を禁止し、代わりに、より安全な方法を提供しています。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** タブで、**\[条件付きコンパイル シンボル\]** ボックスに、定義するシンボルを入力します。  たとえば、次のコード例を使用している場合は、テキスト ボックスに「`xx`」と入力します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>」を参照してください。  
  
## 使用例  
  
```  
// preprocessor_define.cs  
// compile with: /define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
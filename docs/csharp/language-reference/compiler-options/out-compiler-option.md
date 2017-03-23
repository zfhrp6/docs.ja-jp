---
title: "/out (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/out"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/out compiler option [C#]"
  - "out compiler option [C#]"
  - "-out compiler option [C#]"
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /out (C# Compiler Options)
**\/out** オプションは、出力ファイルの名前を指定します。  
  
## 構文  
  
```  
/out:filename  
```  
  
## Arguments  
 `filename`  
 コンパイラで作成される出力ファイルの名前。  
  
## 解説  
 コマンド ラインでは、コンパイルに対して複数の出力ファイルを指定できます。  **\/out** オプションの後に、1 つ以上のソース コード ファイルを指定します。  **\/out** オプションの後に指定されたソース コード ファイルはすべて、その **\/out** オプションに指定された出力ファイルにコンパイルされます。  
  
 作成するファイルについて、フルネームと拡張子を指定します。  
  
 出力ファイルの名前を指定しない場合は、次のように処理されます。  
  
-   .exe の名前は、**Main** メソッドを含むソース コード ファイルと同じになります。  
  
-   .dll または .netmodule は最初のソース ファイルの名前を指定します。  
  
 ある出力ファイルのコンパイルに使用されるソース コード ファイルは、同じコンパイルで別の出力ファイルにコンパイルできません。  
  
 複数の出力ファイルを 1 回のコマンド ライン コンパイルで作成する場合、アセンブリにできるのは、出力ファイルのうちの 1 ファイルだけであり、暗黙にまたは **\/out** を使用して明示的に指定した最初の出力ファイルだけがアセンブリになります。  
  
 コンパイルで作成されたモジュールはすべて、そのコンパイルで作成されたアセンブリに関連付けられるファイルになります。  [ildasm.exe](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md) を使用してアセンブリ マニフェストを表示し、関連付けられたファイルを確認してください。  
  
 target オプションに exe ファイルを指定してフレンド アセンブリを追加するには、\/out コンパイラ オプションが必要です。  詳細については、「[フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[アセンブリ名\]** プロパティを変更します。  
  
     このコンパイラ オプションをプログラムから設定するには: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> は読み取り専用のプロパティです。プロジェクトの種類 \(exe、ライブラリなど\) と、アセンブリ名の組み合わせに基づいて決定されます。  これらのプロパティの一方または両方を変更するには、出力ファイル名を設定する必要があります。  
  
## 使用例  
 `t.cs` をコンパイルして出力ファイル `t.exe` を作成し、`t2.cs` をビルドしてモジュール出力ファイル `mymodule.netmodule` を作成するには、次のコードを使用します。  
  
```  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [フレンド アセンブリ](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
---
title: "/win32icon (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/win32icon"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32icon compiler option [C#]"
  - "/win32icon compiler option [C#]"
  - "-win32icon compiler option [C#]"
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# /win32icon (C# Compiler Options)
**\/win32icon** オプションは、出力ファイルにエクスプローラーで必要な外観を与える .ico ファイルを出力ファイルに挿入します。  
  
## 構文  
  
```  
/win32icon:filename  
```  
  
## Arguments  
 `filename`  
 出力ファイルに加える .ico ファイル。  
  
## 解説  
 .ico ファイルを作成できます [リソース コンパイラ](http://go.microsoft.com/fwlink/?LinkId=148370)。  リソース コンパイラは Visual C\+\+ プログラムをコンパイルするときに呼び出され、.ico ファイルは .rc ファイルから作成されます。  
  
 .NET Framework のリソース ファイルの参照については、「[\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)」、アタッチについては「[\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)」を参照してください。  .res ファイルのインポートについては、「[\/win32res \(Win32 リソース ファイルのインポート\)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[アプリケーション アイコン\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、.ico ファイル `rf.ico` をアタッチして `in.exe` を生成するには、次のコードを使用します。  
  
```  
csc /win32icon:rf.ico in.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
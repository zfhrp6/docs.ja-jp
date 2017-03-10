---
title: "/win32res (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/win32res"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "win32res compiler option"
  - "/win32res compiler option [C#]"
  - "-win32res compiler option [C#]"
  - "win32res compiler option [C#]"
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# /win32res (C# Compiler Options)
**\/win32res** オプションは、Win32 リソースを出力ファイルに挿入します。  
  
## 構文  
  
```  
/win32res:filename  
```  
  
## Arguments  
 `filename`  
 出力ファイルに加えるリソース ファイル。  
  
## 解説  
 Win32 リソース ファイルを作成できます [リソース コンパイラ](http://go.microsoft.com/fwlink/?LinkId=148370)。  リソース コンパイラは、Visual C\+\+ プログラムをコンパイルするときに呼び出されます。.res ファイルは .rc ファイルから作成されます。  
  
 Win32 リソース ファイル エクスプローラーでアプリケーションを識別するときに役立つ、バージョンやビットマップ \(アイコン\) の情報を含めることができます。  **\/win32res** を指定しない場合は、アセンブリのバージョンに基づくバージョン情報がコンパイラによって生成されます。  
  
 .NET Framework のリソース ファイルの参照については、「[\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)」、アタッチについては「[\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[アプリケーション\]** プロパティ ページをクリックします。  
  
3.  **\[リソース ファイル\]** をクリックし、コンボ ボックスを使用してファイルを選択します。  
  
## 使用例  
 `in.cs` をコンパイルし、Win32 リソース ファイル `rf.res` をアタッチして `in.exe` を生成する例を次に示します。  
  
```  
csc /win32res:rf.res in.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
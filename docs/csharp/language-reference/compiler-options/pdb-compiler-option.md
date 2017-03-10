---
title: "/pdb (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/pdb"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-pdb compiler option [C#]"
  - "pdb compiler option [C#]"
  - "/pdb compiler option [C#]"
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 8
---
# /pdb (C# Compiler Options)
**\/pdb** コンパイラ オプションでは、デバッグ シンボル ファイルの名前と場所を指定します。  
  
## 構文  
  
```  
/pdb:filename  
```  
  
## Arguments  
 `filename`  
 デバッグ シンボル ファイルの名前と場所。  
  
## 解説  
 [\/debug \(Emit Debugging Information\)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) を指定すると、コンパイラにより、出力ファイル \(.exe または .dll\) が作成されるのと同じディレクトリに、出力ファイルと同じ名前の .pdb ファイルが作成されます。  
  
 **\/pdb** を使用すると、.pdb ファイルに既定以外のファイル名と場所を指定できます。  
  
 このコンパイラ オプションは、Visual Studio 開発環境で設定することも、プログラムから変更することもできません。  
  
## 使用例  
 `t.cs` をコンパイルし、tt.pdb という名前の .pdb ファイルを作成します。  
  
```  
csc /debug /pdb:tt t.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
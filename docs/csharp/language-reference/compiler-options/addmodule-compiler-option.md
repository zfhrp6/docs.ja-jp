---
title: "/addmodule (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/addmodule"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/addmodule compiler option [C#]"
  - "-addmodule compiler option [C#]"
  - "addmodule compiler option [C#]"
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /addmodule (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

このオプションを指定すると、target:module スイッチで生成されたモジュールが現在のコンパイルに追加されます。  
  
## 構文  
  
```  
/addmodule:file[;file2]  
```  
  
## Arguments  
 `file`, `file2`  
 メタデータを含む出力ファイル。  このファイルにアセンブリ マニフェストを含めることはできません。  複数のファイルをインポートする場合は、コンマまたはセミコロンでファイル名を区切ります。  
  
## 解説  
 **\/addmodule** を使用して追加されたすべてのモジュールは、実行時に出力ファイルと同じディレクトリに配置されている必要があります。  つまり、コンパイル時には任意のディレクトリのモジュールを指定できますが、実行時に指定するモジュールはアプリケーション ディレクトリ内に配置する必要があります。  実行時にモジュールがアプリケーション ディレクトリ内に存在しない場合は、<xref:System.TypeLoadException> になります。  
  
 `file` にアセンブリを含めることはできません。  たとえば、[\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) を使用して出力ファイルが作成された場合、そのメタデータは **\/addmodule** を使用してインポートできます。  
  
 出力ファイルが **\/target:module** 以外の **\/target** オプションを使用して作成された場合、そのメタデータは **\/addmodule** ではインポートできませんが、[\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) を使用してインポートできます。  
  
 このコンパイラ オプションは Visual Studio では使用できないため、プロジェクトではモジュールを参照できません。  また、このコンパイラ オプションは、コードからは変更できません。  
  
## 使用例  
 ソース ファイル `input.cs` をコンパイルし、`metad1.netmodule` および `metad2.netmodule` からメタデータを追加して `out.exe` を作成するには、次のコードを使用します。  
  
```  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [マルチファイル アセンブリ](../Topic/Multifile%20Assemblies.md)   
 [方法 : マルチファイル アセンブリをビルドする](../Topic/How%20to:%20Build%20a%20Multifile%20Assembly.md)
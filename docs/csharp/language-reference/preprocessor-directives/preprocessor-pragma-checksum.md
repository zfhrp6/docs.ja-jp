---
title: "#pragma checksum (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#pragma checksum"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma チェックサム [C#]"
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# #pragma checksum (C# リファレンス)
[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] ページのデバッグに使用するソース ファイルのチェックサムを生成します。  
  
## 構文  
  
```  
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### パラメーター  
 `"filename"`  
 変更または更新を監視する必要があるファイルの名前。  
  
 `"{guid}"`  
 ファイルのグローバル一意識別子 \(GUID: Globally Unique Identifier\)。  
  
 `"checksum_bytes"`  
 チェックサムのバイトを表す 16 進形式の文字列。  偶数の 16 進数であることが必要です。  奇数の数値を指定すると、コンパイル時に警告が出力され、ディレクティブが無視されます。  
  
## 解説  
 Visual Studio デバッガーは、常に正しいソースを検出することを目的としてチェックサムを使用します。  コンパイラはソース ファイルのチェックサムを計算し、プログラム データベース \(PDB\) ファイルに出力します。  デバッガーは、その PDB を使用して、ソース ファイルについて算出されたチェックサムとの比較を行います。  
  
 この方法は、[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] プロジェクトには使用できません。算出されたチェックサムは、.aspx ファイルではなく、生成されたソース ファイルを対象としているためです。  この問題を解決するために、`#pragma checksum` によって [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] ページのチェックサムがサポートされています。  
  
 [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] で [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] プロジェクトを作成すると、生成されるソース ファイルに .aspx ファイルのチェックサムが含められます。ソースは、この .aspx ファイルから生成されます。  次に、コンパイラがこの情報を PDB ファイルに書き込みます。  
  
 ファイルに `#pragma checksum` ディレクティブが見つからない場合、コンパイラはチェックサムを計算し、その値を PDB ファイルに書き込みます。  
  
## 使用例  
  
```  
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)
---
title: "/filealign (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/filealign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/alignment compiler option [C#]"
  - "filealign compiler option [C#]"
  - "-filealign compiler option [C#]"
  - "/sections compiler option [C#]"
  - "alignment compiler option [C#]"
  - "sections compiler option [C#]"
  - "-sections compiler option [C#]"
  - "/filealign compiler option [C#]"
  - "file sharing [C#]"
  - "-alignment compiler option [C#]"
  - "section alignment [C#]"
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# /filealign (C# Compiler Options)
**\/filealign** オプションを使用すると、出力ファイル内のセクションのサイズを指定できます。  
  
## 構文  
  
```  
/filealign:number  
```  
  
## Arguments  
 `number`  
 出力ファイル内のセクションのサイズを指定する値。  有効値は、512、1024、2048、4096、および 8192 です。  これらの値はバイト単位です。  
  
## 解説  
 各セクションは、**\/filealign** 値の倍数となる境界ごとに配置されます。  固定された既定値はありません。  **\/filealign** が指定されていない場合は、共通言語ランタイムによりコンパイル時に既定値が選択されます。  
  
 セクションのサイズを指定すると、出力ファイルのサイズに影響します。  セクションのサイズの変更は、容量の小さなデバイス上で動作するプログラムに対して有効な場合があります。  
  
 出力ファイルのセクションに関する情報を参照するには、[DUMPBIN](/visual-cpp/build/reference/dumpbin-options) を使用します。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  **\[ファイル アライメント\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
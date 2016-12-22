---
title: "/langversion (C# Compiler Options) | Microsoft Docs"
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
  - "/langversion"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/langversion compiler option [C#]"
  - "-langversion compiler option [C#]"
  - "langversion compiler option [C#]"
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: 33
caps.handback.revision: 33
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /langversion (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンパイラが、選択された C\# の言語仕様に含まれている構文のみを受け入れるようにします。  
  
## 構文  
  
```  
/langversion:option  
```  
  
## Arguments  
 `option`  
 有効な値は、次のとおりです。  
  
|オプション|説明|  
|-----------|--------|  
|default|コンパイラは、すべての有効な言語構文を受け入れます。|  
|\[ISO\-1\]|コンパイラは、ISO\/IEC 23270:2003 C\# の言語仕様に含まれている構文のみを受け入れます。|  
|ISO\-2|コンパイラは、ISO\/IEC 23270:2006 C\# の言語仕様に含まれている構文のみを受け入れます。  この仕様は、Web サイトで参照できます [ISO](http://go.microsoft.com/fwlink/?LinkId=144406)。|  
|3|コンパイラは、バージョン 3.0 の [C\# 言語仕様](../../../visual-basic/reference/language-specification.md) に含まれている構文のみを受け入れます。|  
  
## 解説  
 C\# アプリケーションによって参照されるメタデータは、**\/langversion** コンパイラ オプションの影響を受けません。  
  
 C\# コンパイラの各バージョンには言語仕様の拡張機能が含まれているため、**\/langversion** は、コンパイラの以前のバージョンと同等の機能を提供しません。  
  
 どの **\/langversion** 設定を使用する場合でも、.exe や .dll を作成するには、共通言語ランタイムの現在のバージョンを使用します。  ただし、**\/langversion:ISO\-1** に従って動作するフレンド アセンブリと [\/moduleassemblyname \(Specify Friend Assembly for Module\)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) は例外です。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  **\[言語バージョン\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [C\# 言語仕様](../../../visual-basic/reference/language-specification.md)
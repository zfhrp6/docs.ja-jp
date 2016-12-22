---
title: "/warnaserror (C# Compiler Options) | Microsoft Docs"
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
  - "/warnaserror"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/warnaserror compiler option [C#]"
  - "-warnaserror compiler option [C#]"
  - "warnaserror compiler option [C#]"
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warnaserror (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/warnaserror\+** オプションは、すべての警告をエラーとして扱います。  
  
## 構文  
  
```  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## 解説  
 通常は警告としてレポートされるメッセージがエラーとしてレポートされ、ビルド処理が中断します。出力ファイルはビルドされません。  
  
 既定では、警告が出力ファイルの生成を妨げない、**\/warnaserror\-** が有効です。  **\/warnaserror\+** と同じ機能を持つ **\/warnaserror** は、警告をエラーとして扱います。  
  
 また、エラーと見なす警告の番号をコンマ区切りで指定することにより、一部の特定の警告だけをエラーとして扱うこともできます。  
  
 コンパイラで表示する警告のレベルを指定するには、[\/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) を使用します。  特定の警告を無効にするには、[\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) を使用します。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  **\[警告をエラーとして扱う\]** プロパティを変更します。  
  
     このコンパイラ オプションをコードから設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、コンパイラで警告を表示しないようにする例を次に示します。  
  
```  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
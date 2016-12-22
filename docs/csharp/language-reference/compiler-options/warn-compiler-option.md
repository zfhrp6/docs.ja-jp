---
title: "/warn (C# Compiler Options) | Microsoft Docs"
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
  - "/warn"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "warning level [C#]"
  - "/w compiler option [C#]"
  - "-w compiler option [C#]"
  - "-warn compiler option [C#]"
  - "/warn compiler option [C#]"
  - "w compiler option [C#]"
  - "warn compiler option [C#]"
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /warn (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/warn** オプションは、コンパイラが表示する警告レベルを指定します。  
  
## 構文  
  
```  
/warn:option  
```  
  
## Arguments  
 `option`  
 コンパイルで表示させる警告のレベルです。値が小さいほど、表示される警告が増え、重大度の高い警告だけが表示されます。また、値が大きいほど、より多くの警告が表示されます。  次の 0 ～ 4 の値を指定できます。  
  
|警告レベル|説明|  
|-----------|--------|  
|0|すべての警告メッセージの出力をオフにします。|  
|1|重大な警告メッセージを表示します。|  
|2|レベル 1 の警告に加えて、より重大度が低いいくつかの警告を表示します。表示される警告には、クラス メンバーが非表示になっていることについての警告などがあります。|  
|3|レベル 2 の警告に加えて、それより重大度が低いいくつかの警告を表示します。これには、常に `true` または `false` になる式に関する警告などが含まれます。|  
|4 \(既定\)|レベル 3 のすべての警告と、情報を提供するだけの警告を表示します。|  
  
## 解説  
 ヘルプ索引でエラー コードを検索することにより、エラーまたは警告に関する情報を参照できます。  エラーまたは警告に関する情報を入手するための他の方法については、「[C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)」を参照してください。  
  
 すべての警告をエラーとして扱うには、[\/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) を使用します。  特定の警告を無効にするには、[\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) を使用します。  
  
 **\/w** は **\/warn** の省略形です。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  **\[警告レベル\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>」を参照してください。  
  
## 使用例  
 `in.cs` をコンパイルし、コンパイラでレベル 1 の警告だけを表示する例を次に示します。  
  
```  
csc /warn:1 in.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
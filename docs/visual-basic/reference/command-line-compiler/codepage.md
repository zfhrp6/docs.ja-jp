---
title: "/codepage (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/codepage compiler option [Visual Basic]"
  - "codepage compiler option [Visual Basic]"
  - "-codepage compiler option [Visual Basic]"
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /codepage (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。  
  
## 構文  
  
```  
/codepage:id  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`id`|必須。  コンパイラは、`id` で指定されたコード ページを使用して、ソース ファイルのエンコーディングを解釈します。|  
  
## 解説  
 特定のエンコーディングで保存されたソース コードをコンパイルするには、`/codepage` を使用して、使用するコード ページを指定します。  `/codepage` オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。  詳細については、「[.NET Framework における文字エンコーディング](../Topic/Character%20Encoding%20in%20the%20.NET%20Framework.md)」を参照してください。  
  
 `/codepage` オプションは、ソース コード ファイルの保存時に、現在の ANSI コード ページ、Unicode、またはシグネチャ付きの UTF\-8 が使用された場合は不要です。  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] では、ユーザーが **\[エンコード\]** ダイアログ ボックスで他のエンコーディングを指定しない限り、既定で現在の ANSI コード ページを使用してすべてのソース コード ファイルが保存されます。  他のコード ページで保存されたソース コード ファイルを [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で開くときは、 **\[エンコード\]** ダイアログ ボックスが使用されます。  
  
> [!NOTE]
>  `/codepage` オプションは [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 開発環境内では利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
---
title: "/nostdlib (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nostdlib"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nostdlib compiler option [C#]"
  - "-nostdlib compiler option [C#]"
  - "/nostdlib compiler option [C#]"
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# /nostdlib (C# Compiler Options)
**\/nostdlib** は、System 名前空間の全体を定義する mscorlib.dll がインポートされないようにします。  
  
## 構文  
  
```  
/nostdlib[+ | -]  
```  
  
## 解説  
 独自の System 名前空間およびオブジェクトを定義または作成する場合は、このオプションを使用します。  
  
 **\/nostdlib** を指定しないと、**\/nostdlib\-** を指定したことと同じで、mscorlib.dll がプログラムにインポートされます。**\/nostdlib** を指定することは、**\/nostdlib\+** を指定することと同じです。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  **\[mscorlib.dll を参照しない\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>」をご覧ください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)
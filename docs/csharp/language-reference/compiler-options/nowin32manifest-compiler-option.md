---
title: "/nowin32manifest (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/nowin32manifest"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "nowin32manifest compiler option [C#]"
  - "-nowin32manifest compiler option [C#]"
  - "/nowin32manifest compiler option [C#]"
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /nowin32manifest (C# Compiler Options)
**\/nowin32manifest** オプションを使用すると、実行可能ファイルへのアプリケーション マニフェストの埋め込みを行わないようコンパイラに対して指示できます。  
  
## 構文  
  
```  
/nowin32manifest  
```  
  
## 解説  
 このオプションを使用すると、アプリケーションは Windows Vista の仮想化に従います。ただし、Win32 リソース ファイルで、または後のビルド手順で、アプリケーション マニフェストを指定した場合を除きます。  仮想化の詳細については、「[New UAC Technologies for Windows Vista](http://msdn.microsoft.com/ja-jp/80efa4c7-3904-45c5-82e8-2d558fe67db9)」を参照してください。  
  
 Visual Studio の**アプリケーションのプロパティ** ページで、**\[マニフェスト\]** ドロップダウン リストの **\[マニフェストなしでアプリケーションを作成します\]** をクリックしてこのオプションを設定します。  詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(C\#\)](/visual-studio/ide/reference/application-page-project-designer-csharp)」を参照してください。  
  
 マニフェストの作成の詳細については、「[\/win32manifest \(Import a Custom Win32 Manifest File\)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
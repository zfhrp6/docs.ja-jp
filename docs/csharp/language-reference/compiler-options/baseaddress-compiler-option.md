---
title: "/baseaddress (C# Compiler Options) | Microsoft Docs"
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
  - "/dllbase"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "baseaddress compiler option [C#]"
  - "/baseaddress compiler option [C#]"
  - "-baseaddress compiler option [C#]"
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /baseaddress (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/baseaddress** オプションを使用すると、DLL を読み込むベース アドレスを指定できます。  、このオプションを使用する理由と参照しときに詳細について [アプリケーションの起動時間の短縮](http://go.microsoft.com/fwlink/?LinkId=107043) に関する [ラリー Osterman's WebLog](http://go.microsoft.com/fwlink/?LinkId=107044)。  
  
## 構文  
  
```  
/baseaddress:address  
```  
  
## Arguments  
 `address`  
 DLL のベース アドレス。  このアドレスは、10 進数、16 進数、または 8 進数で指定できます。  
  
## 解説  
 DLL の既定のベース アドレスは、.NET Framework 共通言語ランタイムによって設定されます。  
  
 このアドレスの下位ワードは丸められることに注意してください。  たとえば、0x11110001 と指定すると、丸められて 0x11110000 になります。  
  
 DLL の署名プロセスを完了するには、\-R オプションを指定した SN.EXE を使用します。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  DLL のベース アドレス プロパティを変更します。  
  
     このコンパイラ オプションをコードから設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>」を参照してください。  
  
## 参照  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
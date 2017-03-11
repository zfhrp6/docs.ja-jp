---
title: "Bad checksum value, non hex digits or odd number of hex digits | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc42033"
  - "vbc42033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42033"
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Bad checksum value, non hex digits or odd number of hex digits
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

チェックサムの値に無効な 16 進数が含まれるか、桁数が奇数です。  
  
 ASP.NET は Visual Basic のソース ファイル \(拡張子 .vb\) を生成するとき、チェックサムを計算して `#externalchecksum` で指定された隠しソース ファイルに格納します。  ユーザーが同じ目的で .vb ファイルを生成することもできますが、このプロセスは内部使用のままにしておくことをお勧めします。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **Error ID:** BC42033  
  
### このエラーを解決するには  
  
1.  ASP.NET が Visual Basic ソース ファイルを生成している場合は、プロジェクト ビルドを再起動してください。  
  
2.  再起動してもこの警告が続く場合は、ASP.NET をインストールし直してもう一度ビルドしてください。  
  
3.  それでも警告が続くか、ASP.NET を使用していない場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
## 参照  
 [ASP.NET Overview](../Topic/ASP.NET%20Overview.md)   
 [ご意見](/visual-studio/ide/talk-to-us)
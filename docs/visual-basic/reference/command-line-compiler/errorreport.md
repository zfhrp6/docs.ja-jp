---
title: "/errorreport | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-errorreport compiler option [Visual Basic]"
  - "/errorreport compiler option [Visual Basic]"
  - "errorreport compiler option [Visual Basic]"
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /errorreport
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラが内部コンパイラ エラーを出力する方法を指定します。  
  
## 構文  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## 解説  
 このオプションは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 内部コンパイル エラー \(ICE: Internal Compiler Error\) を Microsoft の [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] チームに報告する便利な方法を提供します。  既定で、コンパイラは情報を Microsoft に送信しません。  ただし、内部コンパイル エラーが発生した場合、このオプションを使って Microsoft に報告できます。  Microsoft のエンジニアは、この情報を基に原因を特定し、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の次のリリースの改善に役立てます。  
  
 ユーザーが使用できるレポート送信機能は、使用しているコンピューターやユーザー ポリシーのアクセス許可に応じて異なります。  
  
 次の表に、`/errorreport` オプションの働きをまとめます。  
  
|||  
|-|-|  
|オプション|\[動作\]|  
|`prompt`|内部コンパイル エラーが発生すると、コンパイラで収集されたデータがそのままの形でダイアログ ボックスに表示されます。  エラー レポートに機密情報が含まれているかどうかを確認し、レポートを Microsoft に送信するかどうかを決定できます。  送信することを決定し、コンピューターおよびユーザーのポリシー設定でもこの措置が許容される場合は、コンパイラからデータが Microsoft に送信されます。|  
|`queue`|エラー レポートをキューに配置します。  管理者権限を使ってログインすると、前回のログイン以降に発生したエラーを報告できます。エラー レポートを送信するためのダイアログ ボックスは、3 日に 1 度表示されます。  `/errorreport` オプションを指定しなかった場合の既定の動作がこれです。|  
|`send`|内部コンパイル エラーが発生し、コンピューターおよびユーザーのポリシー設定で情報の送信が許容される場合は、コンパイラからデータが Microsoft に送信されます。<br /><br /> オプション `/errorReport:send` は、エラー情報を Microsoft に自動的に送信しようとします。  このオプションは、レジストリに依存します。  レジストリで適切な値を設定する方法の詳細については、「[How to Turn on Automatic Error Reporting in Visual Studio 2008 Command\-line Tools \(Visual Studio 2008 コマンド ライン ツールでエラーの自動報告を有効にする方法\)](http://go.microsoft.com/fwlink/?LinkID=184695)」を参照してください。|  
|`none`|内部コンパイル エラーが発生した場合、エラーの情報を収集することも、Microsoft に情報を送信することもしません。|  
  
 コンパイラからは、エラー発生時のスタックを含むデータが送信されます。スタックには、通常、一部のソース コードが含まれます。  `/errorreport` を [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) オプションと一緒に指定すると、ソース ファイル全体が送信されます。  
  
 このオプションを [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) オプションと一緒に使用すると Microsoft のエンジニアがエラーを再現しやすくなるので、この組み合わせは最適です。  
  
> [!NOTE]
>  `/errorreport` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 次のコード例は、`T2.vb` をコンパイルしようとします。内部コンパイル エラーが発生すると、コンパイラからはエラー レポートを Microsoft に送信するかどうかを確認するメッセージが表示されます。  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
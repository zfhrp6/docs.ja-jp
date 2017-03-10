---
title: "A startup form has not been specified | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_NoStartupForm"
dev_langs: 
  - "VB"
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# A startup form has not been specified
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アプリケーションで <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスが使用されますが、スタートアップ フォームが指定されていません。  
  
 これは、プロジェクト デザイナーで **\[アプリケーション フレームワークを有効にする\]** チェック ボックスがオンに設定されているが、**スタートアップ フォーム**が指定されていない場合に発生します。  詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
### このエラーを解決するには  
  
1.  アプリケーションのスタートアップ オブジェクトを指定します。  
  
     詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> メソッドをオーバーライドして <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> プロパティをスタートアップ フォームに設定します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>   
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
---
title: "Accessing Application Forms (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "forms, communicating between"
  - "application forms, accessing"
  - "forms, accessing one from another"
  - "My.Forms object"
  - "forms, accessing all open"
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Accessing Application Forms (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Forms` オブジェクトを使用すると、アプリケーションのプロジェクトで宣言されている各 Windows フォームのインスタンスに簡単にアクセスできます。  また、`My.Application` オブジェクトのプロパティを使用して、アプリケーションのスプラッシュ スクリーンやメイン フォームにアクセスしたり、アプリケーションで開いているフォームのリストを取得したりできます。  
  
## タスク  
 次の表は、アプリケーションのフォームへのアクセス方法を示す例の一覧です。  
  
|||  
|-|-|  
|目的|参照項目|  
|アプリケーション内で、あるフォームから別のフォームにアクセスする。|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|アプリケーションで開いているすべてのフォームのタイトルを表示する。|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|アプリケーションの起動時にステータス情報でスプラッシュ スクリーンを更新する。|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)
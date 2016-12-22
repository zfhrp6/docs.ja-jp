---
title: "Rapid Application Development with My.Resources and My.Settings (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "My.Settings object, developing applications"
  - "rapid application development (RAD), My.Resources"
  - "rapid application development (RAD), My.Settings"
  - "My.Resources object, developing applications"
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Rapid Application Development with My.Resources and My.Settings (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`My.Resources` オブジェクトを使用すると、アプリケーションのリソースへのアクセスが可能になり、アプリケーションに必要なリソースを動的に取得できるようになります。  
  
## リソースの取得  
 オーディオ ファイル、アイコン、イメージ、文字列などの多数のリソースを `My.Resources` オブジェクトを介して取得できます。  たとえば、アプリケーションのカルチャ固有のリソース ファイルにアクセスできます。  次の例は、アプリケーションのリソース ファイルに格納された `Form1Icon` という名前のアイコンを、フォームのアイコンに設定します。  
  
 [!code-vb[VbVbcnMy#7](../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/rapid-application-development-with-my-resources-and-my-settings_1.vb)]  
  
 `My.Resources` オブジェクトはグローバルなリソースだけを公開します。  フォームに関連付けられたリソース ファイルへのアクセスはできません。  フォームのリソースには、フォームからアクセスする必要があります。  詳細については、「[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/ja-jp/9a96220d-a19b-4de0-9f48-01e5d82679e5)」を参照してください。  
  
 同様に、`My.Settings` オブジェクトはアプリケーションの設定値へのアクセスを提供し、これによって、プロパティの設定値およびアプリケーションに関するその他の情報を動的に格納および取得できます。  詳細については、「[My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)」および「[My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)」を参照してください。  
  
## 参照  
 [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)   
 [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Accessing Application Settings](../../../visual-basic/developing-apps/programming/app-settings/accessing-application-settings.md)
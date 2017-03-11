---
title: "Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.WebServices object, developing applications"
  - "My.Forms object, developing applications"
  - "rapid application development (RAD), My.Forms"
  - "rapid application development (RAD), My.WebServices"
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Default Object Instances Provided by My.Forms and My.WebServices (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md) および [My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md) オブジェクトは、アプリケーションで使用されるフォーム、データ ソース、および XML Web サービスへのアクセスを提供します。  このアクセスは、これらの各オブジェクトがそれぞれの*既定インスタンス*のコレクションを提供することで実現します。  
  
## 既定インスタンス  
 既定インスタンスとは、ランタイムが提供するクラスのインスタンスで、`Dim` ステートメントおよび `New` ステートメントを使用して宣言およびインスタンス化する必要はありません。  次の例は、`Form1` という名前の <xref:System.Windows.Forms.Form> クラスのインスタンスを宣言およびインスタンス化した方法と、`My.Forms` を通じてこの <xref:System.Windows.Forms.Form> クラスの既定インスタンスを取得できるようにする方法を具体的に示しています。  
  
 [!code-vb[VbVbcnMy#5](../../../visual-basic/developing-apps/development-with-my/codesnippet/visualbasic/default-object-instances_1.vb)]  
  
 [!code-vb[VbVbcnMy#6](../../../visual-basic/developing-apps/development-with-my/codesnippet/visualbasic/default-object-instances_2.vb)]  
  
 `My.Forms` オブジェクトは、プロジェクト内に存在するすべての `Form` クラスの既定インスタンスのコレクションを返します。  同様に、`My.WebServices` は、アプリケーション内で参照を作成したすべての Web サービスのプロキシ クラスの既定インスタンスを提供します。  
  
## 参照  
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
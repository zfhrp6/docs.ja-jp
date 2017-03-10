---
title: "Development with My (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.MyWpfExtension.Windows"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My object"
  - "My namespace"
  - "My feature"
  - "Visual Basic, programming in"
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Development with My (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic には、RAD \(Rapid Application Development\) のための強力な新機能が用意されており、生産性と使いやすさを向上できます。  そうした機能の 1 つが `My` です。アプリケーションおよびその実行時環境に関連する情報や、既定のオブジェクトのインスタンスへのアクセスを実現します。  この情報は、IntelliSense を介して検出できる形式で構成されており、用途に応じて論理的に記述されます。  
  
 `My` のトップレベルのメンバーはオブジェクトとして公開されています。  各オブジェクトは、名前空間や `Shared` メンバーを持つクラスに対して同様に動作し、関連するメンバーを公開します。  
  
 この表は、`My` のトップレベルのオブジェクトと、それぞれの間の関係を示します。  
  
 ![My のオブジェクト モデル](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.png "MyObjModel")  
  
## このセクションの内容  
 [Performing Tasks with My.Application, My.Computer, and My.User](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 `My` の中心となる、`My.Application`、`My.Computer`、および `My.User` の 3 つのオブジェクトについて説明します。情報および機能へのアクセスを提供するオブジェクトです。  
  
 [Default Object Instances Provided by My.Forms and My.WebServices](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 `My.Forms` オブジェクトおよび `My.WebServices` オブジェクトについて説明します。アプリケーションで使用するフォーム、データ ソース、および XML Web サービスへのアクセスを提供するオブジェクトです。  
  
 [Rapid Application Development with My.Resources and My.Settings](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 `My.Resources` オブジェクトおよび `My.Settings` オブジェクトについて説明します。アプリケーションのリソースおよび設定へのアクセスを提供するオブジェクトです。  
  
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーションの起動\/終了モデルについて説明します。  
  
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 プロジェクトの各種類でどの `My` 機能を利用できるかについて詳細を示します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)   
 [How My Depends on Project Type](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
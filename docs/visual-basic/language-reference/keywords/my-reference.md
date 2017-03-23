---
title: "My Reference (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My feature"
  - "My reference"
ms.assetid: 6f803bd7-21ff-4569-b1fe-b00a6678b1e3
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# My Reference (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My` 機能を使うと、頻繁に使用するメソッド、プロパティ、およびイベントにわかりやすい方法でアクセスできるため、プログラムを短い時間で簡単に作成できます。  次の表に、`My` に含まれるオブジェクトと、各オブジェクトを使って実行できる操作をまとめます。  
  
|**動作**|**Object**|  
|------------|----------------|  
|アプリケーションの情報とサービスにアクセスします。|`My.Application` オブジェクトは、次のクラスで構成されます。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> は、すべてのプロジェクトで使用できるメンバーを提供します。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> は、Windows フォーム アプリケーションで使用できるメンバーを提供します。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> には、コンソール アプリケーションで使用できるメンバーを提供します。|  
|ホスト コンピューターとそのリソース、サービス、およびデータにアクセスします。|`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\)|  
|現在のプロジェクトのフォームにアクセスします。|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|アプリケーション ログにアクセスします。|`My.Application.Log` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>\)|  
|現在の Web 要求にアクセスします。|[My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)|  
|リソース要素にアクセスします。|[My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)|  
|現在の Web 応答にアクセスします。|[My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)|  
|ユーザーとアプリケーションのレベル設定にアクセスします。|[My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)|  
|現在のユーザーのセキュリティ コンテキストにアクセスします。|`My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\)|  
|現在のプロジェクトから参照される XML Web サービスにアクセスします。|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
  
## 参照  
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)   
 [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md)
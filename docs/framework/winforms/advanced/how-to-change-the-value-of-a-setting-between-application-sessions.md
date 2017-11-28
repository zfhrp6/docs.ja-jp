---
title: "方法 : アプリケーション セッション間で設定値を変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2dff90e499ce421f372137903daf34c09c21d5c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-setting-between-application-sessions"></a>方法 : アプリケーション セッション間で設定値を変更する
ときに、アプリケーションをコンパイルして、展開後に、アプリケーション セッション間での設定の値を変更することができます。 たとえば、適切なデータベースの場所を指す接続文字列を変更することができます。 アプリケーションをコンパイルして、展開後にデザイン時ツールが使用できないために、ファイルに手動で設定値を変更する必要があります。  
  
### <a name="to-change-the-value-of-a-setting-between-application-sessions"></a>アプリケーション セッション間での設定の値を変更するには  
  
1.  メモ帳または他のテキストまたは XML エディターを使用して、アプリケーションを使用して関連する .config ファイルを開きます。  
  
2.  変更する設定のエントリを探します。 次に示す例のようになります。  
  
    ```xml  
    <setting name="Setting1" serializeAs="String" >  
       <value>My Setting Value</value>  
    </setting>  
    ```  
  
3.  設定の新しい値を入力し、ファイルを保存します。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

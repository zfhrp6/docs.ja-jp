---
title: '方法 : アプリケーション セッション間で設定値を変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], changing
- application settings [Windows Forms], between application sessions
ms.assetid: 1a85911f-97b2-476c-930b-83379edd890c
ms.openlocfilehash: 383f72f223fb92170d16a9538c94e67825009abb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523411"
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

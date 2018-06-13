---
title: My.Settings オブジェクト
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 54176ae6706311b17227c7dc21a5060c9b369753
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603033"
---
# <a name="mysettings-object"></a>My.Settings オブジェクト
プロパティと、アプリケーションの設定にアクセスするためのメソッドを提供します。  
  
## <a name="remarks"></a>コメント  
 `My.Settings`オブジェクトがアプリケーションの設定にアクセスできるようにし、動的に格納およびプロパティの設定と、アプリケーションの他の情報を取得することができます。 詳細については、「[アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)」を参照してください。  
  
## <a name="properties"></a>プロパティ  
 `My.Settings` オブジェクトのプロパティを使用すると、アプリケーションの設定にアクセスできます。 を追加または削除の設定を使用して、**設定デザイナー**です。  
  
 各設定には、**名前**、**型**、**スコープ**、および**値**、これらの設定を決定し、方法各設定にアクセスするプロパティ表示されます、`My.Settings`オブジェクト。  
  
-   **名前**プロパティの名前を指定します。  
  
-   **型**プロパティの種類を決定します。  
  
-   **スコープ**プロパティは読み取り専用のかどうかを示します。 値が場合**アプリケーション**、プロパティは読み取り専用です。 値の場合**ユーザー**、プロパティが読み取り/書き込みです。  
  
-   **値**プロパティの既定値です。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|---|---|  
|`Reload`|最後に保存された値からユーザーの設定を再読み込みします。|  
|`Save`|現在のユーザー設定を保存します。|  
  
 `My.Settings`オブジェクトは、高度なプロパティおよびから継承されたメソッドにも提供、<xref:System.Configuration.ApplicationSettingsBase>クラスです。  
  
## <a name="tasks"></a>[タスク]  
 次の表に、関連するタスクの例については、`My.Settings`オブジェクト。  
  
|終了|解決方法については、|  
|---|---|  
|アプリケーション設定を読み取り|[方法: Visual Basic でアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|ユーザー設定を変更します。|[方法: Visual Basic でユーザー設定を変更する](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|ユーザー設定します。|[方法: Visual Basic でユーザー設定を永続化する](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|ユーザー設定のプロパティ グリッドを作成します。|[方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>例  
 次の例は、`Nickname` の設定値を表示します。  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-settings-object_1.vb)]  
  
 この例を実行するには、アプリケーションで `String` 型の `Nickname` を設定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Configuration.ApplicationSettingsBase>  
 [方法: Visual Basic でアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)  
 [方法: Visual Basic でユーザー設定を変更する](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)  
 [方法: Visual Basic でユーザー設定を永続化する](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)  
 [方法: Visual Basic でユーザー設定のためのプロパティ グリッドを作成する](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)  
 [アプリケーションの設定の管理 (.NET)](/visualstudio/ide/managing-application-settings-dotnet)

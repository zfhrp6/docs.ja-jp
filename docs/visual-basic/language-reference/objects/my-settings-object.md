---
title: "My.Settings オブジェクト | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.MySettingsProperty.Settings"
  - "My.Settings"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Settings オブジェクト"
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# My.Settings オブジェクト
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アプリケーションの設定へのアクセスのプロパティとメソッドを提供します。  
  
## <a name="remarks"></a>コメント  
  `My.Settings` オブジェクトでは、アプリケーションの設定にアクセスし、動的に格納およびプロパティの設定と、アプリケーションの他の情報を取得することができます。 詳細については、次を参照してください。 [を管理するアプリケーションの設定 (.NET)](/visual-studio/ide/managing-application-settings-dotnet)します。  
  
## <a name="properties"></a>プロパティ  
 プロパティ、 `My.Settings` オブジェクトは、アプリケーションの設定にアクセスを提供します。 を追加または削除の設定を使用して、 **設定デザイナー**します。  
  
 各設定では、 **名前**, 、**型**, 、**スコープ**, 、および **値**, 、これらの設定は、各設定にアクセスするプロパティを表示する方法を決定し、 `My.Settings` オブジェクト。  
  
-   **名前** プロパティの名前を指定します。  
  
-   **型** プロパティの種類を決定します。  
  
-   **スコープ** プロパティは読み取り専用のかどうかを示します。 値の場合 **アプリケーション**, 、プロパティは読み取り専用です。 値の場合 **ユーザー**, 、プロパティが読み取り/書き込みです。  
  
-   **値** プロパティの既定値です。  
  
## <a name="methods"></a>メソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|`Reload`|最後に保存されている値からユーザーの設定を再読み込みします。|  
|`Save`|現在のユーザー設定を保存します。|  
  
  `My.Settings` オブジェクトは、高度なプロパティおよびから継承されたメソッドにも提供、 <xref:System.Configuration.ApplicationSettingsBase> クラスです。  
  
## <a name="tasks"></a>タスク  
 次の表に、関連するタスクの例については、 `My.Settings` オブジェクトです。  
  
|||  
|-|-|  
|目的|参照トピック|  
|アプリケーション設定を読み取る|[方法: Visual Basic でのアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|ユーザー設定を変更します。|[方法: Visual Basic でのユーザー設定を変更します。](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|ユーザー設定します。|[方法: Visual Basic でのユーザー設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|ユーザー設定のプロパティ グリッドを作成します。|[方法: Visual Basic でのユーザー設定のプロパティ グリッドを作成します。](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a>例  
 この例の値を表示、 `Nickname` 設定します。  
  
 [!code-vb[VbVbalrMyResources#14](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/visualbasic/VbVbalrMyResources2/Form1.vb#14)]  
  
 この例を実行するには、アプリケーションが必要な `Nickname` 型の設定 `String`します。  
  
## <a name="see-also"></a>「  
 <xref:System.Configuration.ApplicationSettingsBase>   
 [方法: Visual Basic でのアプリケーション設定を読み取る](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)   
 [方法: Visual Basic でのユーザー設定を変更します。](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [方法: Visual Basic でのユーザー設定](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [方法: Visual Basic でのユーザー設定のプロパティ グリッドを作成します。](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [アプリケーション設定 (.NET) を管理します。](/visual-studio/ide/managing-application-settings-dotnet)
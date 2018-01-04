---
title: "方法 : 実行時に設定を C# で読み取る"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], reading
- application settings [Windows Forms], run time
- application settings [Windows Forms], C#
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85dc3a2c97b8fe5003c6026874dbdcaa9af89d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-read-settings-at-run-time-with-c"></a>方法 : 実行時に設定を C# で読み取る #
アプリケーション スコープの設定とユーザー スコープの設定は、どちらも実行時に Properties オブジェクトを使用して読み取ることができます。 Properties オブジェクトは、プロジェクトのすべての既定の設定を、Properties.Settings.Default メンバーを介して公開します。  
  
### <a name="to-read-settings-at-run-time-with-c"></a>実行時に設定を C# で読み取るには  
  
-   Properties.Settings.Default メンバーを介して適切な設定にアクセスします。 BackColor プロパティに `myColor` という名前の設定を割り当てる方法を次の例に示します。 この例を実行する前に、`myColor` という名前の `System.Drawing.Color` 型の設定を含む設定ファイルを作成しておく必要があります。 設定ファイルを作成する方法の詳細については、次を参照してください。[操作方法: デザイン時に新しい設定の作成](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)です。  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## <a name="see-also"></a>参照  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [方法: 実行時にユーザー設定を C# で書き込む](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

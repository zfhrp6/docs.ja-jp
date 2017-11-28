---
title: "方法 : 実行時にユーザー設定を C# で書き込む"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5966aef77c994d2657bd282ad15e8f59a64eeb47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>方法 : 実行時にユーザー設定を C# で書き込む #
アプリケーション スコープの設定は読み取り専用であり、デザイン時、またはアプリケーション セッション間に .config ファイルを変更することによってのみ変更できます。 ただし、ユーザー スコープの設定は、プロパティ値を変更する場合と同様に、実行時に書き込むことができます。 新しい値は、アプリケーションのセッションの実行中に永続化します。 Save メソッドを呼び出すことによって、アプリケーション セッション間で、設定の変更を永続化することができます。  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>方法 : 実行時にユーザー設定を C# で書き込んで永続化する  
  
1.  この設定にアクセスし、この例で示すように、新しい値を割り当てます。  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  アプリケーション セッション間で、設定の変更を永続化する場合は、この例で示すように Save メソッドを呼び出します。  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     ユーザー設定は、ユーザーの非表示のローカル アプリケーション データ フォルダーのサブフォルダー内のファイルに保存されます。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [方法: 実行時に設定を C# で読み取る](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)

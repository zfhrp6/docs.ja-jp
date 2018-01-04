---
title: "方法: アプリケーション間でドラッグ アンド ドロップ操作を実行する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 514c283575ca54e74d23ae31d3590979be2c3ef0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>方法: アプリケーション間でドラッグ アンド ドロップ操作を実行する
アプリケーション間でのドラッグ アンド ドロップ操作の実行は、アプリケーション内での場合と同じですが、両方のアプリケーションが <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> プロパティと <xref:System.Windows.Forms.DragEventArgs.Effect%2A> プロパティの間で確立された "契約" に従って動作する必要があります。  
  
 次の手順では、作成した Windows ベースのアプリケーションと、Windows オペレーティング システムに含まれるワードパッドというワード プロセッサを使用して、アプリケーション間でのドラッグ アンド ドロップ操作を行います。 ワードパッドには、ドラッグ アンド ドロップされたテキストに対して実行できる処理のセットが定義されています。コードを記述する Windows ベースのアプリケーションはこれらの効果に従って動作するため、ドラッグ アンド ドロップ操作を正常に完了できます。  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>アプリケーション間でドラッグ アンド ドロップ手順を実行するには  
  
1.  新しい Windows フォーム アプリケーションを作成します。  
  
2.  フォームに <xref:System.Windows.Forms.TextBox> コントロールを追加します。  
  
3.  ドロップされたデータを受け取るように <xref:System.Windows.Forms.TextBox> コントロールを設定します。  
  
     詳細については、次を参照してください。[チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)です。  
  
4.  作成した Windows ベースのアプリケーションを実行し、アプリケーションの実行中にワードパッドを起動します。  
  
     ワードパッドは、Windows によってインストールされるテキスト エディターであり、ドラッグ アンド ドロップ操作をサポートします。 キーを押してアクセス、**開始**ボタンをクリックし**実行**、」と入力し、`WordPad`のテキスト ボックスに、**実行**をクリックしてダイアログボックス**OK**です。  
  
5.  ワードパッドが起動したら、テキストの文字列を入力します。  
  
6.  マウスを使用してテキストを選択し、選択したテキストを Windows ベースのアプリケーションの <xref:System.Windows.Forms.TextBox> コントロールにドラッグします。  
  
     マウスを <xref:System.Windows.Forms.TextBox> コントロールに移動すると (そして、その結果 <xref:System.Windows.Forms.Control.DragEnter> イベントが発生すると)、マウス ポインターの形が変化し、選択したテキストを <xref:System.Windows.Forms.TextBox> コントロールにドロップできます。  
  
     また、テキスト文字列をワードパッドにドラッグ アンド ドロップできるように <xref:System.Windows.Forms.TextBox> コントロールを設定することもできます。 詳細については、次を参照してください。[チュートリアル: Windows フォームにおけるドラッグ アンド ドロップ操作の実行](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)です。  
  
## <a name="see-also"></a>参照  
 [方法: クリップボードにデータを追加する](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [方法: クリップボードからデータを取得する](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)

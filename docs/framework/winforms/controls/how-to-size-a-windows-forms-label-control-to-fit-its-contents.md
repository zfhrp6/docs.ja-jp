---
title: "方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2c34506ca33af80b83f365893e56a5a9d437b89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>方法 : Windows フォーム Label コントロールのサイズを内容に合わせて変更する
Windows フォーム<xref:System.Windows.Forms.Label>コントロールは、単一行または複数の行を指定できますしたりできるか、固定サイズで、キャプション、それに合わせて自体を自動的に変更できます。 <xref:System.Windows.Forms.Label.AutoSize%2A>プロパティは、拡大または縮小のキャプションに合わせてコントロールのサイズが、実行時に、キャプションが変更される場合に特に便利です。  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>内容に合わせて動的にサイズを変更するラベル コントロールを作成するには  
  
1.  設定の<xref:System.Windows.Forms.Label.AutoSize%2A>プロパティを`true`です。  
  
 場合<xref:System.Windows.Forms.Label.AutoSize%2A>に設定されている`false`、指定した単語、<xref:System.Windows.Forms.Label.Text%2A>プロパティは、可能であれば、次の行に折り返されますが、コントロールは拡張されません。  
  
## <a name="see-also"></a>参照  
 [方法: Windows フォームの Label コントロールでアクセス キーを作成する](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Label コントロールの概要](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Label コントロール](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)

---
title: "方法 : Windows フォームを印刷する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c50b1f47d207334160ed12674ee8efb1390fb84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-windows-form"></a>方法 : Windows フォームを印刷する
開発プロセスの一環として、通常はする、Windows フォームのコピーを印刷します。 次のコード例を使用して現在のフォームのコピーを印刷する方法を示しています、<xref:System.Drawing.Graphics.CopyFromScreen%2A>メソッドです。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 これは、完全なコード例を含む、`Main`メソッドです。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   プリンターへのアクセス許可がありません。  
  
-   プリンターをインストールすることはありません。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 このコード例を実行するためには、コンピューターで使用するプリンターにアクセスする権限が必要です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Drawing.Printing.PrintDocument>  
 [方法: GDI+ を使用してイメージをレンダリングする](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [方法: Windows フォームでグラフィックスを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)

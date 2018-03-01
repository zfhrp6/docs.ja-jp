---
title: "PrintDocument コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 414a7972550558b40403b7f4cbfd9a49194666be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="printdocument-component-overview-windows-forms"></a>PrintDocument コンポーネントの概要 (Windows フォーム)
Windows フォーム [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) コンポーネントを使用して、印刷対象を示すプロパティを設定し、Windows ベースのアプリケーション内でドキュメントを印刷できます。 このコンポーネントは、ドキュメント印刷のあらゆる側面を制御するために、[PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) コンポーネントと組み合わせて使用できます。  
  
## <a name="working-with-the-printdocument-component"></a>PrintDocument コンポーネントの操作  
 2 つの主なシナリオが関係する、<xref:System.Drawing.Printing.PrintDocument>コンポーネントします。  
  
-   簡易印刷ジョブ (個々のテキスト ファイルを印刷する場合など)。 このようなケースで追加すること、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを Windows フォームは、その後でファイルを出力するプログラミングのロジックを追加、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント ハンドラー。 プログラミング ロジックは、最後に、<xref:System.Drawing.Printing.PrintDocument.Print%2A>文書を印刷する方法です。 このメソッドは、送信、<xref:System.Drawing.Graphics>に含まれるオブジェクト、<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>のプロパティ、<xref:System.Drawing.Printing.PrintPageEventArgs>プリンターへのクラスです。 使用して、テキスト ドキュメントを印刷する方法を示す例については、<xref:System.Drawing.Printing.PrintDocument>コンポーネントを参照してください[する方法: Windows フォームで複数ページのテキスト ファイルを印刷](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)です。  
  
-   より複雑な印刷ジョブ (作成した印刷ロジックを再利用する場合など)。 このような場合は、新しいコンポーネントを派生させる、<xref:System.Drawing.Printing.PrintDocument>コンポーネントおよびオーバーライド (を参照してください[オーバーライド](~/docs/visual-basic/language-reference/modifiers/overrides.md)Visual basic の場合または[オーバーライド](~/docs/csharp/language-reference/keywords/override.md)C# の場合)、<xref:System.Drawing.Printing.PrintDocument.PrintPage>イベント。  
  
 フォームに追加されたとき、<xref:System.Drawing.Printing.PrintDocument>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)

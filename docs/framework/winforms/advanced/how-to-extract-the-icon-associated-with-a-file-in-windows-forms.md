---
title: '方法 : Windows フォームでファイルに関連付けられているアイコンを抽出する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a file name and its file type icon in a ListView control [Windows Forms]
- file name extension icons [Windows Forms], displaying in a ListView
- extracting icons associated with a file type [Windows Forms]
ms.assetid: 88e2ad8b-c34f-415a-84f2-dad756b5c928
ms.openlocfilehash: 21bce2f630649afb59272362a7f40055855ed512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522667"
---
# <a name="how-to-extract-the-icon-associated-with-a-file-in-windows-forms"></a>方法 : Windows フォームでファイルに関連付けられているアイコンを抽出する
多くのファイルには、関連付けられているファイルの種類の視覚的に表示されるアイコンが埋め込まれています。 たとえば、Microsoft Word ドキュメントには、Word 文書として識別されるアイコンが含まれます。 ファイルを表示する、テーブル コントロールまたはリスト コントロールで、ときに各ファイル名の横にあるファイルの種類を表すアイコンを表示することがあります。 使用して簡単に行うことができます、<xref:System.Drawing.Icon.ExtractAssociatedIcon%2A>メソッドです。  
  
## <a name="example"></a>例  
 次のコード例をファイルに関連付けられたアイコンを抽出して、ファイル名と関連付けられているアイコンで表示する方法を示しています、<xref:System.Windows.Forms.ListView>コントロール。  
  
 [!code-csharp[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Icon.ExtractAssociatedIconEx#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Icon.ExtractAssociatedIconEx/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 例をコンパイルするには。  
  
-   Windows フォームと呼び出しに上記のコードを貼り付けます、`ExtractAssociatedIconExample`フォームのコンス トラクターからのメソッドまたは<xref:System.Windows.Forms.Form.Load>イベント処理メソッドです。  
  
     フォームをインポートすることを確認する必要があります、<xref:System.IO>名前空間。  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)

---
title: "方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する"
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
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f524bab55527bf9d3c744cb6f50d1df1fc9a2302
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する
2 つのプロパティが、デザイン環境で提供される Windows フォームでコンポーネントを配置する場合:`GenerateMember`と`Modifiers`です。 `GenerateMember`プロパティは、Windows フォーム デザイナーでコンポーネントのメンバー変数を生成するときを指定します。 `Modifiers`プロパティは、そのメンバー変数に割り当てられている、アクセス修飾子。 場合の値、`GenerateMember`プロパティは`false`の値、`Modifiers`プロパティは影響を与えません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>コンポーネントからのメンバーであるかどうかを指定するには  
  
1.  Windows フォーム デザイナーでフォームを開きます。  
  
2.  開く、**ツールボックス**、フォームで、3 つの配置と<xref:System.Windows.Forms.Button>コントロール。  
  
3.  設定、`GenerateMember`と`Modifiers`の各プロパティ<xref:System.Windows.Forms.Button>次の表に従って管理します。  
  
    |ボタン名|GenerateMember 値|修飾子の値|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|変更はありません。|  
  
4.  ソリューションをビルドします。  
  
5.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。  
  
6.  開く、 **Form1**ノード、および、**コード エディター**、開かれている、 **Form1.Designer.vb**または**Form1.Designer.cs**ファイル。 このファイルには、Windows フォーム デザイナーによって生成されます。 コードが含まれています。  
  
7.  3 つのボタンの宣言を検索します。 次のコード例で指定されたの違いを示します、`GenerateMember`と`Modifiers`プロパティです。  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  既定では、Windows フォーム デザイナーが割り当てられます、 `private` (`Friend` Visual basic) 修飾子などのコンテナー コントロールを<xref:System.Windows.Forms.Panel>です。 場合、ベース<xref:System.Windows.Forms.UserControl>または<xref:System.Windows.Forms.Form>コンテナー コントロールを持つ継承されたコントロールとフォームで新しい子を入力することはできません。 解決する基本のコンテナー コントロールの修飾子を変更するには`protected`または`public`です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Button>  
 [Windows フォームのビジュアルの継承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [チュートリアル: ビジュアル継承のデモンストレーション](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [方法: Windows フォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)

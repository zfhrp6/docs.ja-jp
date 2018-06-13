---
title: '方法: プライベート フォント コレクションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: 824d42c40b07e8662395e7a1286b9a5a6112c415
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523085"
---
# <a name="how-to-create-a-private-font-collection"></a>方法: プライベート フォント コレクションを作成する
<xref:System.Drawing.Text.PrivateFontCollection>クラスから継承、<xref:System.Drawing.Text.FontCollection>抽象基本クラスです。 使用することができます、<xref:System.Drawing.Text.PrivateFontCollection>具体的には、アプリケーションのフォントのセットを保持するオブジェクト。 プライベート フォント コレクションには、インストールされているシステム フォントだけでなく、コンピューターにインストールされていないフォントを含めることができます。 プライベート フォント コレクションにフォント ファイルを追加するには、呼び出し、<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A>のメソッド、<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A>のプロパティ、<xref:System.Drawing.Text.PrivateFontCollection>オブジェクトには配列が含まれています<xref:System.Drawing.FontFamily>オブジェクト。  
  
 プライベート フォント コレクション内のフォント ファミリの数は必ずしもをコレクションに追加されているフォント ファイルの数と同じです。 たとえば、ArialBd.tff、Times.tff、および TimesBd.tff ファイル コレクションを追加するとします。 ありますが、3 つのファイル、コレクション内の 2 つだけのファミリ Times.tff と TimesBd.tff 同じファミリに属しているためです。  
  
## <a name="example"></a>例  
 次の例では、次の 3 種類のフォント ファイルを<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
-   C:\\*systemroot*\Fonts\Arial.tff (Arial、正規)  
  
-   C:\\*systemroot*\Fonts\CourBI.tff (媒体使用新しい、太字斜体)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman、太字)  
  
 コードの配列を取得する<xref:System.Drawing.FontFamily>オブジェクトから、<xref:System.Drawing.Text.FontCollection.Families%2A>のプロパティ、<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
 各<xref:System.Drawing.FontFamily>コードの呼び出し、コレクション内のオブジェクト、 <xref:System.Drawing.FontFamily.IsStyleAvailable%2A> (標準、太字、斜体、太字、斜体、下線、取り消し線) のさまざまなスタイルが使用できるかどうかを調べます。 渡される引数、<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>メソッドのメンバーである、<xref:System.Drawing.FontStyle>列挙します。  
  
 特定のファミリ/スタイルの組み合わせがある場合、<xref:System.Drawing.Font>そのファミリとスタイルを使用してオブジェクトを構築します。 渡される最初の引数、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクターは、フォント ファミリ名 (されません、<xref:System.Drawing.FontFamily>オブジェクトの別の形式の場合と同様、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクター)。 後に、<xref:System.Drawing.Font>オブジェクトを構築に渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>スタイルの名前と共に、ファミリ名を表示するクラス。  
  
 次のコードの出力は、次の図に示すように、出力に似ています。  
  
 ![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 次のコード例でプライベート フォント コレクションに追加された) Arial.tff は、Arial 正規スタイルのフォント ファイルです。 ただし、プログラムの出力が Arial フォント ファミリの標準以外の複数の使用可能なスタイルを表示することに注意してください。 これはため[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]太字、斜体、および太字斜体のスタイル標準のスタイルからをシミュレートすることができます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 下線や標準のスタイルから取り消し線も生成できます。  
  
 同様に、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]太字または斜体のスタイルのいずれかから太字斜体のスタイルをシミュレートすることができます。 太字斜体スタイルが回ファミリの使用可能な場合でも、TimesBd.tff (Times New Roman、太字) は、唯一プログラム出力を示しています、コレクション内の回ファイル。  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)

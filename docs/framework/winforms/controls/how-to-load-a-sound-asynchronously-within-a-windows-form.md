---
title: '方法 : Windows フォーム内でサウンドを非同期的に読み込む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SoundPlayer class [Windows Forms], loading sounds asynchronously
- sounds [Windows Forms], loading on separate threads
- threading [Windows Forms], sounds
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
ms.openlocfilehash: 9ebede03a3a9d2cc6db1cda2537bcaf30afcb2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-a-sound-asynchronously-within-a-windows-form"></a>方法 : Windows フォーム内でサウンドを非同期的に読み込む
次のコード例では、URL からサウンドを非同期的に読み込み、新しいスレッド上で再生します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
-   ファイル名 `"http://www.tailspintoys.com/sounds/stop.wav"` を有効なファイル名に置き換えます。  
  
 コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。 この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ファイルの操作は、適切な例外処理ブロックで囲む必要があります。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名が不適切である場合。 たとえば、無効な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException> クラス)。  
  
-   パスが読み取り専用である場合 (<xref:System.IO.IOException> クラス)。  
  
-   パス名が `Nothing` である場合 (<xref:System.ArgumentNullException> クラス)。  
  
-   パス名が長すぎる場合 (<xref:System.IO.PathTooLongException> クラス)。  
  
-   パスが有効でない場合 (<xref:System.IO.DirectoryNotFoundException> クラス)。  
  
-   パスがコロン ":" のみである場合 (<xref:System.NotSupportedException> クラス)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。 たとえば、`Form1.vb` というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 <xref:System.Media.SoundPlayer.LoadCompleted>  
 <xref:System.Media.SoundPlayer.Play%2A>  
 [方法: Windows フォームからサウンドを再生する](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)

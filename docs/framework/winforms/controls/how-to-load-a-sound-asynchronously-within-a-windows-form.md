---
title: "方法 : Windows フォーム内でサウンドを非同期的に読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "サウンドを非同期的にロード SoundPlayer クラス"
  - "サウンド、読み込み (個別のスレッドで)"
  - "スレッド処理 [Windows フォーム]、サウンドします。"
ms.assetid: 3b6a9296-1d5e-4d52-a4ba-94366d6fe302
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : Windows フォーム内でサウンドを非同期的に読み込む
次のコード例では、URL からサウンドを非同期的に読み込み、新しいスレッド上で再生します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.LoadAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.LoadAsync/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
-   ファイル名 `"http://www.tailspintoys.com/sounds/stop.wav"` を有効なファイル名に置き換えます。  
  
 この例のコマンドラインからのビルドについては[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]または[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]を参照してください[コマンドラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)または[使用 csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)します。 また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  参照してください[方法: コンパイルして、完全な Windows フォーム コードの例を使用して Visual Studio を実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))です。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ファイルの操作は、適切な例外処理ブロックで囲む必要があります。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名が不適切である場合。 たとえば、無効な文字が含まれていますか、空白だけが (<xref:System.ArgumentException>クラス)。  
  
-   パスは読み取り専用 (<xref:System.IO.IOException>クラス)。  
  
-   パス名が`Nothing`(<xref:System.ArgumentNullException>クラス)。  
  
-   パス名が長すぎます (<xref:System.IO.PathTooLongException>クラス)。  
  
-   パスが有効ではありません (<xref:System.IO.DirectoryNotFoundException>クラス)。  
  
-   パスがコロンのみ":"(<xref:System.NotSupportedException>クラス)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。 たとえば、`Form1.vb` というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>   
 <xref:System.Media.SoundPlayer.LoadCompleted>   
 <xref:System.Media.SoundPlayer.Play%2A>   
 [方法: Windows フォームからサウンドを再生](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
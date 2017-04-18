---
title: "方法: Visual Basic で利用可能なシリアル ポートを表示する | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cc316600acd5f551dad8fbd4b7260c512231da5e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>方法 : Visual Basic で利用可能なシリアル ポートを表示する
このトピックでは、`My.Computer.Ports` を使用して、コンピュータで利用可能なシリアルポートを [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で表示する方法について説明します。  
  
 使用するポートをユーザーが選択可能とするために、シリアル ポートの名前を <xref:System.Windows.Forms.ListBox> コントロールに格納します。  
  
## <a name="example"></a>例  
 次の例では、`My.Computer.Ports.SerialPortNames` プロパティが返す文字列のすべてについてループします。 これらの文字列は、コンピューターで利用可能なシリアル ポートの名前です。  
  
 通常、利用可能なポートの一覧から、アプリケーションで使用するシリアル ポートをユーザーが選択します。 この例では、シリアル ポートの名前を <xref:System.Windows.Forms.ListBox> コントロールに格納しています。 詳細については、「[ListBox コントロール](http://msdn.microsoft.com/library/b0172473-c5f2-411e-aaa4-c8f17cb5eed4)」を参照してください。  
  
 [!code-vb[VbVbalrMyComputer # 45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 このコード例は IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでは、このコードは「**接続とネットワーク**」にあります。 詳細については、「[Code Snippets](https://docs.microsoft.com/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Windows.Forms.dll へのプロジェクト参照が必要です。  
  
-   <xref:System.Windows.Forms> 名前空間のメンバーへのアクセスが必要です。 コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
-   フォーム上に `ListBox1` という名前の <xref:System.Windows.Forms.ListBox> コントロールが必要です。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 利用可能なシリアル ポートの名前を表示するのに、<xref:System.Windows.Forms.ListBox> コントロールを使用しなくてもかまいません。 代わりに、<xref:System.Windows.Forms.ComboBox> やその他のコントロールを使用することもできます。 ユーザーからの応答が不要なアプリケーションの場合、<xref:System.Windows.Forms.TextBox> コントロールを使用して情報を表示できます。  
  
> [!NOTE]
>  Windows 98 の実行時には、`My.Computer.Ports.SerialPortNames` が返すポート名が正しくない場合があります。 アプリケーション エラーを防ぐには、ポート名を使用してポートを開くときに、`Try...Catch...Finally` ステートメントや `Using` ステートメントなどの例外処理を使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [方法: シリアル ポートに接続されているモデムをダイヤルする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)   
 [方法 : シリアル ポートに文字列を送信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [方法 : シリアル ポートから文字列を受信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)

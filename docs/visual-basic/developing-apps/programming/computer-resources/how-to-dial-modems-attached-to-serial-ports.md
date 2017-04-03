---
title: "方法: Visual Basic で、シリアル ポートに接続されているモデムをダイヤルする | Microsoft Docs"
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
- modems, dialing
- serial ports, dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 4916c7bc3fc60b25dba8386294f11d07346cb358
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>方法 : Visual Basic で、シリアル ポートに接続されているモデムをダイヤルする
このトピックでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で `My.Computer.Ports` を使用してモデムをダイヤルする方法について説明します。  
  
 通常、モデムはコンピューターのいずれかのシリアル ポートに接続されています。 アプリケーションがモデムとやり取りするには、適切なシリアル ポートにコマンドを送信する必要があります。  
  
### <a name="to-dial-a-modem"></a>モデムをダイヤルするには  
  
1.  モデムが接続されているシリアル ポートを確認します。 この例では、モデムが COM1 に接続されていることを前提としています。  
  
2.  `My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。 詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。  
  
     `Using` ブロックを使用すると、アプリケーションは、例外を生成した場合でもシリアル ポートを閉じることができます。 シリアル ポートを操作するコードはすべて、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  コンピューターがモデムからの伝送を受け取る準備ができたことを示しよう `DtrEnable` プロパティを設定します。  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <xref:System.IO.Ports.SerialPort.Write%2A> メソッドを使用して、ダイヤル コマンドと電話番号をシリアル ポート経由でモデムに送信します。  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 このコード例は、IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。 詳細については、「[Code Snippets](https://docs.microsoft.com/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例では、<xref:System?displayProperty=fullName> 名前空間への参照が必要です。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 この例では、モデムが COM1 に接続されていることを前提としています。 コードによって、利用可能なシリアル ポートの一覧から、目的のポートをユーザーが選択できるようにすることをお勧めします。 詳細については、「[方法: 利用可能なシリアル ポートを表示する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」を参照してください。  
  
 この例では、アプリケーションが例外をスローした場合でもポートを閉じられるよう、`Using` ブロックを使用しています。 詳細については、「[sing ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
 この例では、アプリケーションは、モデムをダイヤルした後でシリアル ポートを切断しています。 実際には、モデムとの間でデータの転送が必要となります。 詳細については、「[方法: シリアル ポートから文字列を受信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 <xref:System.IO.Ports.SerialPort?displayProperty=fullName>   
 [方法: シリアル ポートに文字列を送信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)   
 [方法: シリアル ポートから文字列を受信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)   
 [方法 : 利用可能なシリアル ポートを表示する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

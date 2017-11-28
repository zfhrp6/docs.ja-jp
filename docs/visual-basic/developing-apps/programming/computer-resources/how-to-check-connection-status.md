---
title: "方法 : Visual Basic で接続ステータスをチェックする"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Web connections [Visual Basic]
- IsAvailable property [Visual Basic], about IsAvailable
- connections [Visual Basic], checking status
- connection status [Visual Basic]
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 62361b4efff4c53156becf0cd865d262fbef1504
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-check-connection-status-in-visual-basic"></a>方法 : Visual Basic で接続ステータスをチェックする
正常に動作しているネットワーク接続またはインターネット接続がコンピューターにあるかどうかは、<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> プロパティを使って調べることができます。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-check-whether-a-computer-has-a-working-connection"></a>正常に動作している接続がコンピューターにあるかどうかを調べるには  
  
-   `IsAvailable` プロパティが `True` であるか `False` であるかを調べます。 このプロパティのステータスを調べて報告するコードを次に示します。  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     このコード例は、IntelliSense コード スニペットとしても利用できます。 コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>

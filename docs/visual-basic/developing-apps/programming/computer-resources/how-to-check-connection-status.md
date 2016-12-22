---
title: "How to: Check Connection Status in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Web connections"
  - "IsAvailable property, about IsAvailable"
  - "connections, checking status"
  - "connection status"
ms.assetid: 4d9ee8ab-9a6f-4279-ace4-b75afc976a74
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Check Connection Status in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A> プロパティを使用して、コンピューターが有効なネットワーク接続またはインターネット接続をしているかどうかを判断できます。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### コンピューターが有効な接続をしているかどうかをチェックするには  
  
-   `IsAvailable` プロパティが `True` と `False` のどちらであるかを確認します。  次のコードは、プロパティのステータスをチェックし、それを報告します。  
  
     [!code-vb[VbResourceTasks#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-check-connection-status_1.vb)]  
  
     このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[接続とネットワーク\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.IsAvailable%2A>
---
title: "Port Operations in the .NET Framework with Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ports, Visual Basic"
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Port Operations in the .NET Framework with Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:System.IO.Ports?displayProperty=fullName> 名前空間の [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラスを使用して、コンピューターのシリアル ポートにアクセスできます。  最も重要な役割を持つのが <xref:System.IO.Ports.SerialPort> クラスです。このクラスは、同期 I\/O とイベント ドリブン I\/O、ピンの状態とブレーク状態へのアクセス、およびシリアル ドライバーのプロパティへのアクセスを提供します。  これは <xref:System.IO.Stream> オブジェクトでラップでき、<xref:System.IO.Ports.SerialPort.BaseStream%2A> プロパティを通じてアクセスできます。  <xref:System.IO.Ports.SerialPort> を <xref:System.IO.Stream> オブジェクトでラップすると、ストリームを使用するクラスでシリアル ポートにアクセスできます。  この名前空間には、シリアル ポートの制御を簡素化する列挙体が含まれています。  
  
 <xref:System.IO.Ports.SerialPort> オブジェクトを作成するには、<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> メソッドを使用する方法が最も簡単です。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] のクラスを使用して、他の種類のポート \(パラレル ポートや USB ポートなど\) に直接アクセスすることはできません。  
  
## 列挙型  
 この表は、シリアル ポートへのアクセスで使用する主要な列挙体の一覧とその説明です。  
  
|||  
|-|-|  
|列挙型|Description|  
|<xref:System.IO.Ports.Handshake>|<xref:System.IO.Ports.SerialPort> オブジェクトでシリアル ポート通信の確立に使用する制御プロトコルが定められています。|  
|<xref:System.IO.Ports.Parity>|<xref:System.IO.Ports.SerialPort> オブジェクトのパリティ ビットが定められています。|  
|<xref:System.IO.Ports.SerialData>|<xref:System.IO.Ports.SerialPort> オブジェクトのシリアル ポートで受信した文字の種類が定められています。|  
|<xref:System.IO.Ports.SerialError>|<xref:System.IO.Ports.SerialPort> オブジェクトで発生するエラーが定められています。|  
|<xref:System.IO.Ports.SerialPinChange>|<xref:System.IO.Ports.SerialPort> オブジェクトで発生した変更の種類が定められています。|  
|<xref:System.IO.Ports.StopBits>|<xref:System.IO.Ports.SerialPort> オブジェクトで使用されているストップ ビットの数が定められています。|  
  
## 参照  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
---
title: "Visual Basic による .NET Framework でのポート操作"
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
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e01853cba19ffa0a7d9997eef3d25d2b2e3166dd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Visual Basic による .NET Framework でのポート操作
<xref:System.IO.Ports?displayProperty=fullName> 名前空間の [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] クラスを介して、コンピューターのシリアル ポートにアクセスできます。 最も重要な役割を持つのが <xref:System.IO.Ports.SerialPort> クラスです。このクラスにより、同期 I/O とイベント ドリブン I/O のフレームワーク、ピンの状態とブレーク状態へのアクセス、およびシリアル ドライバーのプロパティへのアクセスを使用できます。 このクラスは、<xref:System.IO.Ports.SerialPort.BaseStream%2A> プロパティを通じてアクセス可能な <xref:System.IO.Stream> オブジェクト内にラップできます。 <xref:System.IO.Stream> オブジェクト内で <xref:System.IO.Ports.SerialPort> をラップすることにより、ストリームを使用するクラスからシリアル ポートへのアクセスを実現できます。 名前空間には、シリアル ポートの制御を容易にする列挙型が含まれています。  
  
 最も簡単に <xref:System.IO.Ports.SerialPort> オブジェクトを作成する方法は、<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> メソッドを経由することです。  
  
> [!NOTE]
>  [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] クラスを使用してパラレル ポートや USB ポートなどの他の種類のポートに直接アクセスすることはできません。  
  
## <a name="enumerations"></a>列挙  
 次の表は、シリアル ポートへのアクセスに使用される主な列挙型を一覧にまとめ、説明を加えたものです。  
  
|列挙|説明|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<xref:System.IO.Ports.SerialPort> オブジェクトでのシリアル ポート通信の確立に使用する制御プロトコルを指定します。|  
|<xref:System.IO.Ports.Parity>|<xref:System.IO.Ports.SerialPort> オブジェクトのパリティ ビットを指定します。|  
|<xref:System.IO.Ports.SerialData>|<xref:System.IO.Ports.SerialPort> オブジェクトのシリアル ポートで受信した文字の型を指定します。|  
|<xref:System.IO.Ports.SerialError>|<xref:System.IO.Ports.SerialPort> オブジェクトで発生するエラーを指定します。|  
|<xref:System.IO.Ports.SerialPinChange>|<xref:System.IO.Ports.SerialPort> オブジェクトで発生した変更の種類を指定します。|  
|<xref:System.IO.Ports.StopBits>|<xref:System.IO.Ports.SerialPort> オブジェクトで使用するストップ ビットの数を指定します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Ports>   
 [コンピューターのポートへのアクセス](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)


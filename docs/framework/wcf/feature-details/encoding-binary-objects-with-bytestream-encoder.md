---
title: "バイトストリーム エンコーダーを使用したバイナリ オブジェクトのエンコーディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1516731181a7e60445ce19752c3bb1835cb5897
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>バイトストリーム エンコーダーを使用したバイナリ オブジェクトのエンコーディング
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] による生のバイナリ データの送受信は、<xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> を使用して構成されます。  
  
## <a name="byte-stream-message-encoder-architecture"></a>バイト ストリーム メッセージ エンコーダーのアーキテクチャ  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で使用されるバイナリ メッセージ エンコーダーには、メッセージ内の基になるバイナリ メッセージを処理、検証、または識別する機能がありません。 データ パッケージは、XML にエンコード、送受信、およびデコードされます。 エンコーダーは、トランスポートに渡された後に、メッセージがメッセージ キューに送られる前にデータを処理します。 機能的には、バイナリ エンコーダーが、送信用にメッセージ データを `<binary>` 要素にラップし、そのメッセージが受信された後にこの要素を削除します。  
  
## <a name="using-the-byte-stream-message-encoder"></a>バイト ストリーム メッセージ エンコーダーの使用  
 次の例は、バイト ストリーム メッセージ エンコーダーを実装するサービス コントラクトを示しています。  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 次の例は、呼び出されたサービスを示しています。  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 ルーターなどのメッセージ インフラストラクチャを実装するサービスを使用する場合、そのメッセージは、次の例に示すように、メッセージの検査、検証、およびメッセージとの対話操作のいずれも行うことなく処理されます。  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>シナリオ  
 バイト ストリーム エンコーダーは、次のシナリオに役立ちます。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用してコンピューター間で JPEG イメージを転送する。 このシナリオでは、イメージは外部ソースから転送によって到着し、送信されたデータはイメージを構成する生バイトになります。 サービスはバイナリ データを受信してイメージを表示します。  
  
-   メッセージ キューからの情報の読み取りと処理。 メッセージはメッセージ キュー マネージャーから読み取られ、処理対象のメッセージ キュー チャネルに渡されます。 メッセージ キュー チャネルは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] チャネル スタックでキュー マネージャーとして機能します。  
  
 メッセージをメッセージ キュー チャネルを介して送信する場合、送信者はキュー マネージャーから受信したバイトを制御できません。 受信プロセスで生バイトを読み取ることができない場合、メッセージは不適切な書式として受信され処理されません。受信プロセスは受信したバイトを利用可能な形式に変換する機能があると見なされます。

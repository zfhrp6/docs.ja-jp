---
title: "コントラクトおよびサービスのエラーの指定と処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: handling faults [WCF]
ms.assetid: a9696563-d404-4905-942d-1e0834c26dea
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7be16a899974f325231a4010ad74bc55ee56d2a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-and-handling-faults-in-contracts-and-services"></a>コントラクトおよびサービスのエラーの指定と処理
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションは、マネージ例外オブジェクトを SOAP エラー オブジェクトにマップし、SOAP エラー オブジェクトをマネージ例外オブジェクトにマップすることによって、エラー状態を処理します。 ここでは、エラー状態がカスタムの SOAP エラーとして公開されるようにコントラクトを設計する方法、そのエラーをサービス実装の一部として返す方法、およびクライアントがそのエラーをキャッチする方法を説明します。  
  
## <a name="error-handling-overview"></a>エラー処理の概要  
 すべてのマネージ アプリケーションで、操作エラーは <xref:System.Exception> オブジェクトにより表されます。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションなどの SOAP に基づくアプリケーションでは、サービス メソッドは SOAP エラー メッセージを使用して操作エラー情報を通知します。 SOAP エラーは、サービス操作のメタデータに含まれるメッセージ型です。これにより、クライアントが操作を堅牢かつインタラクティブにするために使用できるエラー コントラクトを作成できます。 また、SOAP エラーは XML 形式でクライアントに伝達されるので、この型システムは相互運用性が高く、あらゆる SOAP プラットフォーム上のクライアントが使用できます。これによって、ユーザーの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションの適用範囲が拡大します。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションは、両方の型のエラー システムで実行されるので、クライアントに送信されるマネージ例外情報は、サービス上で例外から SOAP エラーに変換し、送信後、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントで SOAP エラーからエラー例外に変換する必要があります。 双方向クライアントの場合は、クライアント コントラクトによって SOAP エラーがサービスに返送されることもあります。 いずれの場合も、開発者は、既定のサービス例外の動作を使用することも、例外をエラー メッセージにマップするかどうかを制御することも (その場合はどのようにマップするかを指定することも) できます。  
  
 SOAP エラーの 2 つの型を送信することができます:*宣言*と*宣言されていない*です。 宣言された SOAP エラーは、カスタム SOAP エラーの種類を指定する <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> 属性を含む操作で発生します。 *宣言されていない*操作のコントラクトでは、SOAP エラーは指定されていません。  
  
 <xref:System.ServiceModel.FaultContractAttribute> 属性を使用して、通常の操作中に受信することをクライアントが予期できるすべての SOAP エラーを正式に指定することによって、サービス操作でそのエラーを宣言することを強くお勧めします。 また、SOAP エラーでは、情報の漏えいを最小限に抑えるために、クライアントが知る必要がある情報だけを返すことをお勧めします。  
  
 通常、サービス (および双方向クライアント) は、次の手順に従ってエラー処理をアプリケーションに統合します。  
  
-   例外状態をカスタム SOAP エラーにマップします。  
  
-   クライアントとサービスは、SOAP エラーを例外として送受信します。  
  
 また、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のクライアントとサービスは、デバッグの目的で非宣言 SOAP エラーを使用でき、既定のエラー動作を拡張できます。 以下のセクションで、これらの手順と概念について説明します。  
  
## <a name="map-exceptions-to-soap-faults"></a>SOAP エラーへの例外のマッピング  
 エラー状態の処理操作を作成するための最初の手順は、クライアント アプリケーションにエラーを通知する状態を決定することです。 一部の操作には、その機能に固有のエラー状態があります。 たとえば、`PurchaseOrder` 操作では、発注書の作成が禁止になっている顧客に特定の情報を返すことができます。 また、`Calculator` サービスなどでは、より一般的な `MathFault` SOAP エラーを使用してサービス全体のすべてのエラー状態を記述できます。 サービスのクライアントのエラー状態を特定したら、カスタム SOAP エラーを作成し、エラー状態が発生したときに SOAP エラーを返す操作として、対応する操作をマークします。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]サービスまたはクライアントの開発には、この手順を参照してください[を指定するエラーの定義および](../../../docs/framework/wcf/defining-and-specifying-faults.md)です。  
  
## <a name="clients-and-services-handle-soap-faults-as-exceptions"></a>クライアントとサービスによる例外としての SOAP エラーの処理  
 操作エラー状態を特定し、カスタム SOAP エラーを定義し、そのようなエラーを返す操作にマークすることは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションで正常にエラーを処理するための最初の手順です。 次の手順では、このエラーの送受信を適切に実装します。 通常は、サービスがエラーを送信してクライアント アプリケーションにエラー状態を通知しますが、双方向クライアントが SOAP エラーをサービスに送信することもできます。  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][エラーを送受信する](../../../docs/framework/wcf/sending-and-receiving-faults.md)です。  
  
## <a name="undeclared-soap-faults-and-debugging"></a>非宣言 SOAP エラーとデバッグ  
 宣言 SOAP エラーは、堅牢で相互運用可能な分散アプリケーションを構築するうえで便利です。 ただし、サービス (または双方向クライアント) が非宣言 SOAP エラーを送信することが役立つ場合があります。非宣言 SOAP エラーとは、その操作について Web サービス記述言語 (WSDL) で宣言されていないエラーです。 たとえば、サービスの開発時に予期しない状況が発生する可能性があります。この場合、デバッグのために情報をクライアントに送信することが役立ちます。 また、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> プロパティを `true` に設定して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントが内部のサービス操作例外に関する情報を取得できるようにすることができます。 個々 のエラーの送信とデバッグ動作プロパティの設定の両方がで説明されている[送信と受信エラー](../../../docs/framework/wcf/sending-and-receiving-faults.md)です。  
  
> [!IMPORTANT]
>  マネージ例外が内部アプリケーション情報を開示する可能性があるので、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> を `true` に設定すると、個人の身元を確認できる情報またはその他の機密情報を含む内部サービス操作例外に関する情報を [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントで取得できます。  
>   
>  したがって、<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> を `true` に設定することは、サービス アプリケーションを一時的にデバッグする方法としてのみお勧めできます。 さらに、このようにして未処理のマネージ例外を返すメソッドの WSDL には、<xref:System.ServiceModel.FaultException%601> 型の <xref:System.ServiceModel.ExceptionDetail> のコントラクトが含まれません。 クライアントは、デバッグ情報を適切に取得するために、([!INCLUDE[indigo2](../../../includes/indigo2-md.md)] オブジェクトとして <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> クライアントに返される) 不明な SOAP エラーの可能性について想定しておく必要があります。  
  
## <a name="customizing-error-handling-with-ierrorhandler"></a>IErrorHandler によるエラー処理のカスタマイズ  
 アプリケーション レベルの例外が発生した場合にクライアントへの応答メッセージをカスタマイズする、または応答メッセージが返された後に何らかのカスタム処理を実行するという特別な要件がある場合は、<xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> インターフェイスを実装します。  
  
## <a name="fault-serialization-issues"></a>エラーのシリアル化の問題  
 WCF では、エラー コントラクトを逆シリアル化する場合、最初に SOAP メッセージのエラー コントラクト名とエラー コントラクトの型を一致させようとします。 正しく一致しない場合、使用可能なエラー コントラクトのアルファベット順のリストで互換性のある型を検索します。 2 つのエラー コントラクトが互換性のある型である場合 (たとえば、一方のコントラクトが別のコントラクトのサブクラスである場合)、エラーを逆シリアル化するときに間違った型が使用される場合があります。 このような問題は、エラー コントラクトで名前、名前空間、およびアクションが指定されていない場合に発生します。 このような問題が発生しないようにするには、常に名前、名前空間、およびアクションの属性を指定して、エラー コントラクトを完全修飾するようにしてください。 また、共有基本クラスから派生した関連エラー コントラクトを定義している場合は、新しいメンバーを `[DataMember(IsRequired=true)]` でマークしてください。 この `IsRequired` 属性の詳細については、「<xref:System.Runtime.Serialization.DataMemberAttribute>」を参照してください。 この結果、基本クラスに互換性のある型が指定されなくなり、正しい派生型にエラーが逆シリアル化されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.CommunicationException>  
 <xref:System.ServiceModel.FaultContractAttribute.Action%2A>  
 <xref:System.ServiceModel.FaultException.Code%2A>  
 <xref:System.ServiceModel.FaultException.Reason%2A>  
 <xref:System.ServiceModel.FaultCode.SubCode%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 [エラーの定義と指定](../../../docs/framework/wcf/defining-and-specifying-faults.md)

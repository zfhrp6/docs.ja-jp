---
title: "方法 : セッションを必要とするサービスを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 方法 : セッションを必要とするサービスを作成する
セッションでは、複数のエンドポイント間で共有される状態が作成されます。これにより、クライアントとサービス インスタンス間でのコールバック、マルチホップ セキュリティ、関連付けなどの便利な機能を使用できるようになります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]セッションで[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]、アプリケーションを参照してください[セッションを使用した](../../../../docs/framework/wcf/using-sessions.md)します。  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>バインディングによるセッションのサポートを要求するコントラクトを指定するには  
  
1.  操作を&1; つ以上含むサービス コントラクトを作成します。 サービス コントラクトを作成する方法の例は、次を参照してください。[方法: サービス コントラクトを定義する](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)です。  
  
2.  変更、 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>を設定して、コントラクトを宣言する、 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=fullName>プロパティをいずれか。  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName>場合はこのコントラクトは、セッション内で実行する必要があります。  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName>でこのコントラクトは、セッション内で実行できる場合です。  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName>場合は、セッション内で、このコントラクトを実行しない必要があります。  
  
3.  セッションをサポートするバインディングを使用するようにサービス エンドポイントを構成します。 次の構成例の使用を示しています、 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>をサポートする、WS`-`ReliableMessaging セッションです。  
  
     [!code[SCA.Session#2](../../../../samples/snippets/common/VS_Snippets_CFX/sca.session/common/hostapplication.exe.config#2)]
     [!code-csharp[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
     [!code-vb[SCA.Session#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/hostapplication.exe.config#2)]  
  
## <a name="example"></a>例  
 次のコード例は、コントラクト レベルでのセッション要件を指定して、によってこの要件をサポートするために、構成ファイルを使用する方法を示しています、 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>バインドします。  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]  
  
 [!code[SCA.Session#2](../../../../samples/snippets/common/VS_Snippets_CFX/sca.session/common/hostapplication.exe.config#2)]
 [!code-csharp[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
 [!code-vb[SCA.Session#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/hostapplication.exe.config#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>   
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.SessionMode?displayProperty=fullName>
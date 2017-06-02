---
title: "Windows Communication Foundation のバインディングの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "バインディング [WCF], 概要"
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Windows Communication Foundation のバインディングの概要
バインディングとは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスのエンドポイントへの接続に必要な通信の詳細設定を指定する際に使用するオブジェクトのことです。  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの各エンドポイントでは、バインディングを適切に指定する必要があります。  ここでは、バインディングによって定義される通信の詳細設定、バインディングの要素、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に用意されているバインディング、およびエンドポイントにバインディングを指定する方法について説明します。  
  
## バインディングの定義内容  
 バインディングの情報は非常に基本的にも複雑にもなりえます。  最も基本的なバインディングはトランスポート プロトコル \(HTTP など\) のみを指定したもので、これはエンドポイントへの接続に必ず使用します。  一般的に、バインディングに含まれるエンドポイントへの接続方法を示す情報は、次のカテゴリのいずれかに当てはまります。  
  
 プロトコル  
 使用されているセキュリティ機構 \(信頼性の高いメッセージング機能またはトランザクション コンテキストのフロー設定のいずれか\) を決定します。  
  
 エンコーディング  
 メッセージ エンコーディング \(テキストまたはバイナリなど\) を決定します。  
  
 Transport  
 使用する基本のトランスポート プロトコル \(TCP や HTTP など\) を決定します。  
  
## バインディングの要素  
 バインディングは、基本的に、バインド要素の順序付きスタックで構成されます。各バインド要素では、サービス エンドポイントに接続するために必要な通信情報の一部を指定します。  スタックの 2 つの最も低い層は両方とも必須です。  スタックの一番下にトランスポート バインド要素があり、そのすぐ上にメッセージ エンコーディング仕様を含んだ要素があります。  その他の通信プロトコルを指定するオプションのバインド要素は、この 2 つの必須要素の上に配置されます。  これらのバインド要素とその正確な順序[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)」を参照してください。  
  
## システム標準のバインディング  
 バインディングの情報は複雑になる可能性があり、一部の設定は他の設定と互換性がない場合もあります。  このため、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、システム指定のバインディングが用意されています。  このバインディングは、アプリケーション要件のほとんどに対応するように設計されています。  システム指定のバインディングの例のいくつかを次のクラスで示します。  
  
-   <xref:System.ServiceModel.BasicHttpBinding> : WS\-I Basic Profile 仕様に準拠する Web サービス \(ASP.NET Web サービス ベースのサービスなど\) への接続に適した HTTP プロトコル バインディング。  
  
-   <xref:System.ServiceModel.WSHttpBinding> : WS\-\* プロトコルに準拠するエンドポイントへの接続に適した相互運用可能なバインディング。  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding> : 同じコンピューター上の他の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] エンドポイントへの接続に [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使用するバインディング。  
  
-   <xref:System.ServiceModel.NetMsmqBinding> : キューに置かれたメッセージと他の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] エンドポイントとの接続を作成するために [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使用するバインディング。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 指定のバインディングの完全な一覧と説明については、「[システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。  
  
## 独自のバインディングの使用  
 システム指定のバインディングに、サービス アプリケーションに必要な正しい組み合わせの機能がない場合、独自のバインディングを作成できます。  これには、2 つの方法があります。  <xref:System.ServiceModel.Channels.CustomBinding> オブジェクトを使用して既存のバインド要素から新しいバインディングを作成するか、<xref:System.ServiceModel.Channels.Binding> バインディングから派生することによって完全にユーザー定義のバインディングを作成することができます。  これら 2 つの方法で独自のバインディングを作成する手順[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)」および「[ユーザー定義バインディングの作成](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)」を参照してください。  
  
## バインディングの使用  
 バインディングを使用する際には、次の 2 つの基本手順があります。  
  
1.  バインディングを選択、または定義します。  最も簡単な方法は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に用意されているシステム指定のバインディングを 1 つ選択し、それを既定の設定で使用することです。  また、システム指定のバインディングを選択し、そのプロパティを要件に適した値に再設定することもできます。  別の方法として、カスタム バインディングまたはユーザー定義バインディングを作成し、より高度な制御とカスタマイズを実現することができます。  
  
2.  選択または定義されたバインディングを使用するエンドポイントを作成します。  
  
## コードおよび構成  
 バインディングを定義するには、コードによる方法と構成による方法の 2 とおりがあります。  この 2 つの方法は、システム指定またはカスタムのどちらのバインディングを使用している場合でも有効です。  一般的には、コードを使用すると、開発者がデザイン時にバインディングの定義を完全に制御することになります。  一方、構成を使用する場合は、システム管理者や、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスまたはクライアントのユーザーが、サービス アプリケーションをコンパイルし直すことなくバインディングのパラメーターを変更できます。  通常は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションの展開先の具体的なコンピューター要件を予測する方法がないため、柔軟性のあるこの方法が望まれます。  バインディング情報とアドレス情報をコードに含めないでおくと、これらの情報を変更したときにアプリケーションを再度コンパイルしたり、展開したりする必要がなくなります。  コードで定義したバインディングは、構成で指定したバインディングの後に作成されます。そのため、構成で定義したバインディングはコードで定義したバインディングによって上書きされることに注意してください。  
  
## 参照  
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
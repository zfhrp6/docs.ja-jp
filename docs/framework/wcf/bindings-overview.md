---
title: "Windows Communication Foundation のバインディングの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a131574e0e3de8507a91807d5de2899238c14628
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-bindings-overview"></a>Windows Communication Foundation のバインディングの概要
バインディングとは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスのエンドポイントへの接続に必要な通信の詳細設定を指定する際に使用するオブジェクトのことです。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの各エンドポイントでは、バインディングを適切に指定する必要があります。 ここでは、バインディングによって定義される通信の詳細設定、バインディングの要素、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に用意されているバインディング、およびエンドポイントにバインディングを指定する方法について説明します。  
  
## <a name="what-a-binding-defines"></a>バインディングの定義内容  
 バインディングの情報は非常に基本的にも複雑にもなりえます。 最も基本的なバインディングはトランスポート プロトコル (HTTP など) のみを指定したもので、これはエンドポイントへの接続に必ず使用します。 一般的に、バインディングに含まれるエンドポイントへの接続方法を示す情報は、次のカテゴリのいずれかに当てはまります。  
  
 プロトコル  
 使用されているセキュリティ機構 (信頼性の高いメッセージング機能またはトランザクション コンテキストのフロー設定のいずれか) を決定します。  
  
 エンコーディング  
 メッセージ エンコーディング (テキストまたはバイナリなど) を決定します。  
  
 Transport  
 使用する基本のトランスポート プロトコル (TCP や HTTP など) を決定します。  
  
## <a name="the-elements-of-a-binding"></a>バインディングの要素  
 バインディングは、基本的に、バインド要素の順序付きスタックで構成されます。各バインド要素では、サービス エンドポイントに接続するために必要な通信情報の一部を指定します。 スタックの 2 つの最も低い層は両方とも必須です。 スタックの一番下にトランスポート バインド要素があり、そのすぐ上にメッセージ エンコーディング仕様を含んだ要素があります。 その他の通信プロトコルを指定するオプションのバインド要素は、この 2 つの必須要素の上に配置されます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]これらのバインド要素と、正しい順序に基づいてを参照してください。[カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
## <a name="system-provided-bindings"></a>システム標準のバインディング  
 バインディングの情報は複雑になる可能性があり、一部の設定は他の設定と互換性がない場合もあります。 このため、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、システム指定のバインディングが用意されています。 このバインディングは、アプリケーション要件のほとんどに対応するように設計されています。 システム指定のバインディングの例のいくつかを次のクラスで示します。  
  
-   <xref:System.ServiceModel.BasicHttpBinding> : WS-I Basic Profile 仕様に準拠する Web サービス (ASP.NET Web サービス ベースのサービスなど) への接続に適した HTTP プロトコル バインディング。  
  
-   <xref:System.ServiceModel.WSHttpBinding> : WS-* プロトコルに準拠するエンドポイントへの接続に適した相互運用可能なバインディング。  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding> : 同じコンピューター上の他の [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] エンドポイントへの接続に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用するバインディング。  
  
-   <xref:System.ServiceModel.NetMsmqBinding> : キューに置かれたメッセージと他の [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] エンドポイントとの接続を作成するために [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用するバインディング。  
  
 すべての説明を含む、完全な一覧について、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-バインド」を参照してください提供[システム指定のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)です。  
  
## <a name="using-your-own-bindings"></a>独自のバインディングの使用  
 システム指定のバインディングに、サービス アプリケーションに必要な正しい組み合わせの機能がない場合、独自のバインディングを作成できます。 これには、2 つの方法があります。 <xref:System.ServiceModel.Channels.CustomBinding> オブジェクトを使用して既存のバインド要素から新しいバインディングを作成するか、<xref:System.ServiceModel.Channels.Binding> バインディングから派生することによって完全にユーザー定義のバインディングを作成することができます。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]独自の作成をこれら 2 つの方法を使用したバインディングを参照してください[カスタム バインディング](../../../docs/framework/wcf/extending/custom-bindings.md)と[ユーザー定義バインディング](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)です。  
  
## <a name="using-bindings"></a>バインディングの使用  
 バインディングを使用する際には、次の 2 つの基本手順があります。  
  
1.  バインディングを選択、または定義します。 最も簡単な方法は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に用意されているシステム指定のバインディングを 1 つ選択し、それを既定の設定で使用することです。 また、システム指定のバインディングを選択し、そのプロパティを要件に適した値に再設定することもできます。 別の方法として、カスタム バインディングまたはユーザー定義バインディングを作成し、より高度な制御とカスタマイズを実現することができます。  
  
2.  選択または定義されたバインディングを使用するエンドポイントを作成します。  
  
## <a name="code-and-configuration"></a>コードおよび構成  
 バインディングを定義するには、コードによる方法と構成による方法の 2 とおりがあります。 この 2 つの方法は、システム指定またはカスタムのどちらのバインディングを使用している場合でも有効です。 一般的には、コードを使用すると、開発者がデザイン時にバインディングの定義を完全に制御することになります。 一方、構成を使用する場合は、システム管理者や、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスまたはクライアントのユーザーが、サービス アプリケーションをコンパイルし直すことなくバインディングのパラメーターを変更できます。 通常は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションの展開先の具体的なコンピューター要件を予測する方法がないため、柔軟性のあるこの方法が望まれます。 バインディング情報とアドレス情報をコードに含めないでおくと、これらの情報を変更したときにアプリケーションを再度コンパイルしたり、展開したりする必要がなくなります。 コードで定義したバインディングは、構成で指定したバインディングの後に作成されます。そのため、構成で定義したバインディングはコードで定義したバインディングによって上書きされることに注意してください。  
  
## <a name="see-also"></a>関連項目  
 [サービスとクライアントを構成するためのバインディングの使用](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)

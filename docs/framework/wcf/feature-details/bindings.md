---
title: Windows Communication Foundation バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 373f7feb64d69373630c942750f264d559643a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communcation-foundation-bindings"></a>Windows Communication Foundation バインディング
Windows Communication Foundation (WCF) では、他のソフトウェアと通信するアプリケーション用のソフトウェアが書き込まれる方法を区切ります。 バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定します。 WCF では、バインディングを使用して、バインディングの詳細の大半が通信している双方が合意する必要がありますので、エンドポイントの基になるネットワーク上の表現を生成します。 これを実現する最も簡単な方法は、サービスのクライアントがサービスのエンドポイントと同じバインディングを使用することです。 これを行う方法の詳細については、次を参照してください。 [Windows Communication Foundation サービスを構成してクライアントを使用してバインド](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)です。  
  
 バインディングは、バインド要素のコレクションで構成されます。 各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。 バインディングには、1 つ以上のトランスポート バインド要素、1 つ以上のメッセージ エンコーディング バインド要素 (既定では、トランスポート バインド要素によって提供されます)、および任意の数の他のプロトコル バインド要素が含まれている必要があります。 このように、ランタイムをビルドするプロセスでは、各バインド要素からランタイムにコードを提供できます。  
  
 WCF には、バインド要素の一般的なバインドを含むバインディングが用意されています。 これらのバインディングは、既定の設定で使用することも、ユーザーの要件に応じて既定値を変更することもできます。 これらのシステム指定のバインディングには、バインド要素およびその設定を直接制御できるプロパティが含まれます。 また、バインディングの各バージョンに独自の名前を付けることで、複数のバージョンを同時に使用することもできます。 詳細については、「 [Configuring System-Provided バインド](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)です。  
  
 システム指定のバインディングに用意されていないバインド要素のコレクションが必要になった場合には、その必要なバインド要素のコレクションで構成されるカスタム バインドを作成できます。 このようなカスタム バインドは簡単に作成でき、新しいクラスも必要ありませんが、バインド要素およびその設定を制御するためのプロパティは提供されません。 バインド要素へのアクセスと設定の変更は、バインド要素を含むコレクションを通じて行います。 詳細については、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [システムが提供するバインディングの構成](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 使用し、一般的なシナリオをサポートするために WCF が提供するバインドを変更する方法について説明します。  
  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 コードと構成を使用して宣言で強制的にサービスとクライアントの Windows Communication Foundation (WCF) バインドを定義する方法について説明します。  
  
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <xref:System.ServiceModel.Channels.CustomBinding> の概要と使用する状況について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>関連項目  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)

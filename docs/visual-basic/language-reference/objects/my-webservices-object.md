---
title: "My.WebServices オブジェクト"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords: My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9f2c4017a1df8059f2cc57e7c30a96c474cfda0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mywebservices-object"></a>My.WebServices オブジェクト
作成すると、現在のプロジェクトによって参照される各 XML Web サービスの 1 つのインスタンスにアクセスするには、プロパティを提供します。  
  
## <a name="remarks"></a>コメント  
 `My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。 各インスタンスは要求に応じてインスタンス化されます。 これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。 プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。 プロジェクトに Web サービスを追加する方法の詳細については、次を参照してください。[アプリケーション Web サービスのへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)です。  
  
 `My.WebServices`オブジェクトは、現在のプロジェクトに関連付けられている Web サービスのみを公開します。 参照された Dll で宣言されている Web サービスへのアクセスは提供されません。 DLL を提供する Web サービスにアクセスするには、フォームで Web サービスの修飾名を使用する必要があります*DllName*.*WebServiceName*です。 詳細については、次を参照してください。[アプリケーション Web サービスのへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)です。  
  
 オブジェクトとそのプロパティでは、Web アプリケーションを使用できません。  
  
## <a name="properties"></a>プロパティ  
 各プロパティ、`My.WebServices`オブジェクトが現在のプロジェクトによって参照される Web サービスのインスタンスへのアクセスを提供します。 プロパティの名前は、プロパティがアクセスすると、Web サービスの名前と同じとプロパティの型が、Web サービスの型と同じです。  
  
> [!NOTE]
>  Web サービスへのアクセスのプロパティ名には、名前の競合がある場合*RootNamespace*_*Namespace*\_*ServiceName*です。 たとえば、という 2 つの Web サービス`Service1`です。 ルート名前空間にはこれらのサービスのいずれかのかどうかは`WindowsApplication1`と名前空間に`Namespace1`を使用してそのサービスにアクセスするよう`My.WebServices.WindowsApplication1_Namespace1_Service1`です。  
  
 初めてアクセスしたときの 1 つ、`My.WebServices`オブジェクトのプロパティ、その Web サービスの新しいインスタンスを作成および格納します。 そのプロパティのそれ以降のアクセスは、その Web サービスのインスタンスを返します。  
  
 割り当てることによって、Web サービスの破棄する`Nothing`その Web サービスのプロパティにします。 プロパティ set アクセス操作子が割り当てられます`Nothing`に格納されている値。 以外の任意の値を割り当てる場合`Nothing`プロパティの setter がスローされます、<xref:System.ArgumentException>例外。  
  
 プロパティかどうかをテストすることができます、`My.WebServices`オブジェクトを使用して、Web サービスのインスタンスが格納されて、`Is`または`IsNot`演算子。 これらの演算子を使用するには、プロパティの値をチェックする`Nothing`です。  
  
> [!NOTE]
>  通常、`Is`または`IsNot`オペレーターが、比較を実行するプロパティの値を読み取ることがあります。 ただし場合、プロパティが現在格納`Nothing`プロパティ、Web サービスの新しいインスタンスを作成し、そのインスタンスを返します。 ただし、Visual Basic コンパイラがのプロパティを処理、`My.WebServices`でき、特別に、オブジェクト、`Is`または`IsNot`演算子をその値を変更することがなく、プロパティの状態を確認します。  
  
## <a name="example"></a>例  
 この例では、`FahrenheitToCelsius`のメソッド、 `TemperatureConverter` XML Web サービス、結果を返します。  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 この例を実行するは、プロジェクトがという名前の Web サービスを参照する必要があります`Converter`、およびその Web サービスを公開する必要があります、`ConvertTemperature`メソッドです。 詳細については、次を参照してください。[アプリケーション Web サービスのへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)です。  
  
 このコードは、Web アプリケーション プロジェクトでは機能しません。  
  
## <a name="requirements"></a>要件  
  
### <a name="availability-by-project-type"></a>プロジェクトの種類別の可用性  
  
|プロジェクトの種類|使用可能|  
|---|---|  
|Windows アプリケーション|**はい**|  
|クラス ライブラリ|**はい**|  
|コンソール アプリケーション|**はい**|  
|Windows コントロール ライブラリ|**はい**|  
|Web コントロール ライブラリ|**はい**|  
|Windows サービス|**はい**|  
|Web サイト|いいえ|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [アプリケーションの Web サービスへのアクセス](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)

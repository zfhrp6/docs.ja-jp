---
title: "My.WebServices Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.WebServices"
  - "My.MyProject.WebServices"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.WebServices object"
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# My.WebServices Object
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

現在のプロジェクトから参照する、各 XML Web サービスのインスタンスを作成したり、使用したりするためのプロパティを提供します。  
  
## 解説  
 `My.WebServices` オブジェクトは、現在のプロジェクトから参照されている各 Web サービスのインスタンスを提供します。  各インスタンスは、要求に応じてインスタンス化されます。  これらの Web サービスには、`My.WebServices` オブジェクトのプロパティからアクセスできます。  プロパティの名前は、そのプロパティでアクセスする Web サービスの名前と同じです。  <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> を継承するクラスはすべて Web サービスです。  Web サービスをプロジェクトに追加する方法については、「[Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)」を参照してください。  
  
 `My.WebServices` オブジェクトは、現在のプロジェクトに関連付けられている Web サービスのみを公開します。  参照された DLL 内で宣言されている Web サービスにはアクセスできません。  DLL 内で宣言された Web サービスにアクセスするには、Web サービスの修飾名を使用する必要があります。Web サービスの修飾名は *DllName*.*WebServiceName* という形式になります。  詳細については、「[Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)」を参照してください。  
  
 このオブジェクトとプロパティは、Web アプリケーションでは使用できません。  
  
## プロパティ  
 `My.WebServices` オブジェクトのプロパティを使用すると、現在のプロジェクトから参照されている Web サービスのインスタンスにアクセスできます。  プロパティの名前はそのプロパティがアクセスする Web サービスの名前と同じになり、プロパティの型は Web サービスの型と同じになります。  
  
> [!NOTE]
>  名前の衝突が存在する場合、Web サービスにアクセスするためのプロパティ名は *RootNamespace*\_*Namespace*\_*ServiceName* になります。  たとえば、`Service1` という名前の 2 つの Web サービスがあるものとします。  一方のサービスがルート名前空間 `WindowsApplication1` の `Namespace1` という名前空間に存在する場合、このサービスには `My.WebServices.WindowsApplication1_Namespace1_Service1` を使用してアクセスできます。  
  
 `My.WebServices` オブジェクトのプロパティに初めてアクセスすると、対応する Web サービスの新しいインスタンスが作成され、プロパティに格納されます。  以降は、そのプロパティにアクセスすると Web サービスのインスタンスが返されます。  
  
 Web サービスを破棄するには、その Web サービスを表すプロパティに `Nothing` を代入します。  これにより、プロパティ Set アクセス操作子が格納値に `Nothing` を代入します。  このプロパティに `Nothing` 以外の値を代入した場合は、setter が <xref:System.ArgumentException> 例外をスローします。  
  
 `My.WebServices` オブジェクトのプロパティに Web サービスのインスタンスが格納されているかどうかを調べるには、`Is` または `IsNot` 演算子を使用します。  これらの演算子を使用して、プロパティの値が `Nothing` かどうかを確認します。  
  
> [!NOTE]
>  通常は、`Is` または `IsNot` 演算子が比較を実行するためには、プロパティの値を読み取る必要があります。  しかし、プロパティの現在の値が `Nothing` である場合は、値を読み取ろうとすると Web サービスの新しいインスタンスが作成され、そのインスタンスが返されてしまいます。  そこで、Visual Basic コンパイラは `My.WebServices` オブジェクトのプロパティを特別扱いとし、`Is` または `IsNot` 演算子がプロパティの値を変更せずにプロパティのステータスを確認できるようにしています。  
  
## 使用例  
 この例では、`TemperatureConverter` XML Web サービスの `FahrenheitToCelsius` メソッドを呼び出し、結果を返します。  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/visualbasic/VbVbalrMyWebService/Form1.vb#1)]  
  
 この例を実行するためには、プロジェクトが `Converter` という名前の Web サービスを参照していて、その Web サービスが `ConvertTemperature` メソッドを公開している必要があります。  詳細については、「[Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)」を参照してください。  
  
 このコードは Web アプリケーション プロジェクトでは実行できません。  
  
## 要件  
  
### プロジェクトの種類ごとの可用性  
  
|||  
|-|-|  
|プロジェクトの種類|可用性|  
|Windows アプリケーション|**○**|  
|クラス ライブラリ|**○**|  
|コンソール アプリケーション|**○**|  
|Windows コントロール ライブラリ|**○**|  
|Web コントロール ライブラリ|**○**|  
|Windows サービス|**○**|  
|Web サイト|Ｘ|  
  
## 参照  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>   
 <xref:System.ArgumentException>   
 [Accessing Application Web Services](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
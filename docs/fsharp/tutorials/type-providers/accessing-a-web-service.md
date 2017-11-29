---
title: "チュートリアル - 型プロバイダー (f#) を使用して Web サービスにアクセスします。"
description: "F# 3.0 で使用可能な Web サービス記述言語 (WSDL) 型プロバイダーを使用して WSDL サービスにアクセスする方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>チュートリアル : 型プロバイダーを使用した Web サービスへのアクセス

> [!NOTE]
このガイドでは、f# 3.0 用に作成された、更新されます。  最新のクロスプラットフォームの型プロバイダーについては、[FSharp.Data](http://fsharp.github.io/FSharp.Data/) を参照してください。

> [!NOTE]
API リファレンス リンクで msdn を実行します。  docs.microsoft.com API リファレンスは完全ではありません。

このチュートリアルでは、F# 3.0 で利用可能な Web サービス記述言語 (WSDL) 型プロバイダーを使用して WSDL サービスにアクセスする方法を説明します。 他の .NET 言語では、svcutil.exe を呼び出すか、または Web 参照を追加して Web サービスにアクセスするためのコードを生成します。たとえば、C# プロジェクトの場合は、Visual Studio で svcutil.exe を呼び出します。 F# では、WSDL 型プロバイダーを使用する追加オプションがあるので、WsdlService 型を作成するコードを記述するとすぐに型が生成されて使用できるようになります。 このプロセスは、コードを記述するときに利用できるサービスに依存します。

このチュートリアルでは、次の作業について説明します。 このチュートリアルを正しく行うには、以下の作業を順に行ってください。


- プロジェクトの作成
<br />

- 型プロバイダーの構成
<br />

- Web サービスの呼び出しと結果の処理
<br />


## <a name="creating-the-project"></a>プロジェクトの作成
この手順では、プロジェクトを作成し、WSDL 型プロバイダーを使用するために適切な参照を追加します。


#### <a name="to-create-and-set-up-an-f-project"></a>F# プロジェクトを作成してセットアップするには

1. 新しい F# コンソール アプリケーション プロジェクトを開きます。
<br />

2. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、プロジェクトの**参照** ノードを選択し**参照の追加**です。
<br />

3. **アセンブリ**領域で、選択**Framework**をクリックし、使用可能なアセンブリの一覧で、選択**System.Runtime.Serialization**と**System.ServiceModel**です。
<br />

4. **アセンブリ**領域で、選択**拡張**です。
<br />

5. 使用可能なアセンブリの一覧で選択**FSharp.Data.TypeProviders**を選択し、 **[ok]**をこれらのアセンブリへの参照を追加するボタンをクリックします。
<br />

## <a name="configuring-the-type-provider"></a>型プロバイダーの構成
この手順では、WSDL 型プロバイダーを使用して TerraServer Web サービスの型を生成します。


#### <a name="to-configure-the-type-provider-and-generate-types"></a>型プロバイダーを構成して型を生成するには

1. 型プロバイダーの名前空間を開くには、以下のコード行を追加します。
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. Web サービスで型プロバイダーを呼び出すには、以下のコード行を追加します。 この例では、TerraServer Web サービスを使用します。
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  サービス URI にスペル ミスがある場合、サービス自体が停止している場合、または動作していない場合は、このコード行の下に赤の波線が表示されます。 コードをポイントすると、問題を説明するエラー メッセージが表示されます。 同じ情報を見つけることができます、**エラー一覧**ウィンドウまたは、**出力ウィンドウ**をビルドした後です。
<br />  WSDL 接続の構成設定を指定するには、プロジェクトの app.config ファイルを使用する方法と、型プロバイダーの宣言で静的な型パラメーターを使用する方法の 2 とおりあります。 svcutil.exe を使用すると、適切な構成ファイル要素を生成できます。 Svcutil.exe を使用して、web サービスの構成情報を生成する方法の詳細については、次を参照してください。 [ServiceModel メタデータ ユーティリティ ツールと #40 です。Svcutil.exe &#41;](https://msdn.microsoft.com/library/aa347733.aspx). WSDL 型プロバイダーの静的な型パラメーターの詳細を参照してください。 [WsdlService 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)です。
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>Web サービスの呼び出しと結果の処理
各 Web サービスには、メソッド呼び出しのパラメーターとして使用される独自の型のセットがあります。 この手順では、これらのパラメーターを準備して Web メソッドを呼び出し、返される情報を処理します。


#### <a name="to-call-the-web-service-and-process-the-results"></a>Web サービスを呼び出して結果を処理するには

1. Web サービスにはタイムアウトや機能停止の可能性があるので、例外処理ブロックに Web サービス呼び出しを含める必要があります。 Web サービスからデータを取得するには、次のコードを記述します。
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

Web サービスなどのために必要なデータ型を作成することに注意してください。**場所**と**場所**、WsdlService 入れ子にされた型の型として、 **TerraService**です。
<br />


## <a name="see-also"></a>関連項目
[WsdlService 型プロバイダー](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[型プロバイダー](index.md)

---
title: ML.NET を使用してニューヨークのタクシー運賃を予測する (回帰)
description: 回帰のシナリオで ML.NET を使用する方法について説明します。
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34860706"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>チュートリアル: ML.NET を使用してニューヨークのタクシー運賃を予測する (回帰)

> [!NOTE]
> このトピックでは現在プレビュー段階である ML.NET を参照しており、資料が変更される可能性があります。 詳しくは、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)を参照してください。

このチュートリアルでは、ML.NET を使用して、ニューヨーク市のタクシー運賃を予測する[回帰モデル](../resources/glossary.md#regression)を構築する方法を示します。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習タスクを選択する
> * データを準備して理解する
> * 学習パイプラインを作成する
> * データを読み込んで変換する
> * 学習アルゴリズムを選択する
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

## <a name="prerequisites"></a>必須コンポーネント

* [Visual Studio 2017 15.6 以降](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。

## <a name="understand-the-problem"></a>問題を把握する

この問題の中心となるのは、**ニューヨーク市のタクシー旅行の運賃の予測**です。 一見すると、単に乗車距離に依存すると思われるかもしれません。 しかし、ニューヨークのタクシー会社は追加の乗客数や現金でなくクレジット カードによる支払いなど、その他の要因によって請求額を変えます。

## <a name="select-the-appropriate-machine-learning-task"></a>適切な機械学習タスクを選択する

タクシー運賃を予測するには、最初に適切な機械学習タスクを選択します。 ここでは、データ セット内のその他の要因に基づいて実際の値 (価格を表す倍精度値) を予測しようとしています。 そのため、[**回帰**](../resources/glossary.md#regression)タスクを選択します。

モデルのトレーニングのプロセスでは、最終的な運賃の予測の際に最も大きな影響を与えたデータ セット内の要因を特定します。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「TaxiFarePrediction」と入力し、**[OK]** を選択します。

2. プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。

    **ソリューション エクスプローラー**で、使用するプロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

3. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、使用するプロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

### <a name="prepare-and-understand-your-data"></a>データを準備して理解する

1. [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) データ セットと [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) データ セットをダウンロードして、作成済みの *Data* フォルダーに保存します。 Taxi Trip データ セットは、機械学習モデルをトレーニングします。このデータ セットを使用すると、モデルの正確性を評価できます。 これらのデータ セットは、[NYC TLC Taxi Trip データ セット](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)から取得したものです。

2. ソリューション エクスプローラーで、各 \*.csv ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[常時]** に変更します。

3. **taxi-fare-train.csv** データ セットをコード エディターで開き、最初の行の列ヘッダーを確認します。 各列を確認してください。 データについて把握し、どの列が**特徴**および**ラベル**であるかを確認します。

**ラベル**は、予測しようとしている列の識別子です。 識別された**特徴**は、ラベルを予測するために使用します。

* **vendor_id:** タクシー会社の ID は特徴です。
* **rate_code:** タクシー旅行のレートの種類は特徴です。
* **passenger_count:** 旅行の乗客数は特徴です。
* **trip_time_in_secs:** 旅行の所要時間です。 旅行の所要時間は旅行が終わるまでわかりません。 この列はモデルから除外します。
* **trip_distance:** 旅行距離は特徴です。
* **payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。
* **fare_amount:** 支払った合計タクシー運賃はラベルです。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

最近ダウンロードしたファイルのパスを保持し、モデルを保存する 3 つのグローバル変数を作成する必要があります。

* `_datapath` には、モデルのトレーニングに使用するデータ セットのパスがあります。
* `_testdatapath` には、モデルの評価に使用するデータ セットのパスがあります。
* `_modelpath` には、トレーニング済みのモデルを格納するパスがあります。

`Main` のすぐ上にある行に次のコードを追加して、最近ダウンロードしたファイルを指定します。

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

次に、入力データと予測のためのクラスを作成します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TaxiTrip.cs* に変更します。 次に、**[追加]** を選択します。
1. 新しいファイルに次の `using` ステートメントを追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

既存のクラス定義を削除し、2 つのクラス `TaxiTrip` と `TaxiTripFarePrediction` を含む次のコードを *TaxiTrip.cs* ファイルに追加します。

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` は入力データ セット クラスであり、各データ セット列の定義が含まれています。 `TaxiTripFarePrediction` クラスは、モデルのトレーニング後の予測に使用します。 このクラスには 1 つの浮動小数点 (`FareAmount`) および [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 属性を適用した `Score` が格納されています。

**Program.cs** ファイルに戻ります。 `Main` で、`Console.WriteLine("Hello World!")` を次のコードに置き換えます。

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` メソッドは、モデルをトレーニングします。 次のコードを使用して、`Main` の直下にその関数を作成します。

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a>学習パイプラインを作成する

学習パイプラインは、モデルのトレーニングに必要なすべてのデータとアルゴリズムを読み込みます。 `Train()` メソッドに次のコードを追加します。

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a>データを読み込んで変換する

次に、パイプラインにデータを読み込みます。 最初に作成した `_datapath` をポイントして、.csv ファイルの区切り記号 (,) を指定します。 最後のステップの下にある `Train()` メソッドに次のコードを追加します。

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

作成するコードでは、アンダースコアのない列を参照します。 `ColumnCopier()` 関数を使用して、`FareAmount` 列を "Label" という名前の新しい列にコピーします。 この列は**ラベル**です。

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

**特徴エンジニアリング**を実行してデータを変換し、機械学習でデータを効果的に使用できるようにします。 モデルをトレーニングするアルゴリズムには、**数値**の特徴が必要であるため、カテゴリ データ (`VendorId`、`RateCode`、および `PaymentType`) を数字に変換します。 `CategoricalOneHotVectorizer()` 関数は、これらの各列の値に数値キーを割り当てます。 このコードを追加することで、データを変換します。

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

データ準備の最後の手順は、`ColumnConcatenator()` 関数を使用して、すべての**特徴**を 1 つのベクトルに結合することです。 この必須の手順によって、アルゴリズムが特徴を簡単に処理できるようになります。 次のコードを追加します。

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

`trip_time_in_secs` 列が含まれていないことに注意してください。 既に確認したとおり、この列は有効な予測特徴ではありません。

> [!NOTE]
> これらの手順を成功させるには、前述の指定した順序でパイプラインに追加する必要があります。

## <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

データをパイプラインに追加して正しい入力形式に変換したら、学習アルゴリズム (**ラーナー**) を選択します。 学習アルゴリズムは、モデルをトレーニングします。 この問題に対しては**回帰タスク**を選択済みであるため、**勾配ブースティング**を利用するパイプラインに `FastTreeRegressor()` というラーナーを追加します。

勾配ブースティングは、回帰問題に対応する機械学習の手法です。 この手法では、それぞれの回帰ツリーを段階的に構築します。 また、定義済みの損失関数を使用して、各ステップの誤差を測定し、次の段階で修正します。 結果は予測モデルですが、実際は弱い予測モデルの集合です。 勾配ブースティングについて詳しくは、「[Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression)」(ブーストされたデシジョン ツリー回帰) を参照してください。

前の手順で追加したデータ処理コードの後にある `Train()` メソッドに次のコードを追加します。

```csharp
pipeline.Add(new FastTreeRegressor());
```

前述のすべての手順は個々のステートメントとしてパイプラインに追加しましたが、C# には使いやすいコレクションの初期化構文があるため、パイプラインの作成と初期化が簡単になります。 次のコードを使用して、これまでに追加したコードを `Train()` メソッドに置き換えます。

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>モデルをトレーニングする

最後の手順は、モデルのトレーニングです。 ここまで、パイプライン内の項目は何も実行されていません。 `pipeline.Train<T_Input, T_Output>()` 関数は、定義済みの `TaxiTrip`クラス型を受け入れて、`TaxiTripFarePrediction` 型を出力します。 この最後のコード部分を `Train()` 関数に追加します。

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

以上です。 これで機械学習モデルのトレーニングが終了し、ニューヨーク市のタクシー運賃を予測できるようになりました。 それでは、モデルの正確性と使い方を確認してみましょう。

## <a name="save-the-model"></a>モデルを保存する

次の手順に進む前に、`Train()` 関数の末尾に次のコードを追加して、モデルを .zip ファイルに保存します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

`model.WriteAsync()` の呼び出しに `await` ステートメントを追加した場合は、`Train()` メソッドを `Task` を返す非同期メソッドに変更する必要があります。 次のコードに示すように、`Train` のシグネチャを変更します。

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

`Train` メソッドの戻り値の型を変更した場合は、次のコードに示すように、`Main` メソッドで `Train` を呼び出すコードに `await` を追加する必要があります。

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

`Main` メソッドに `await` を追加した場合は、`Main` メソッドに `async` 修飾子が必要です。このメソッドは `Task` を返す必要があります。

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

また、次の using ステートメントをファイルの先頭に追加する必要もあります。

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

`async Main` メソッドは C# 7.1 の新機能であり、プロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。
そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。 **[OK]** ボタンを選択します。

## <a name="evaluate-the-model"></a>モデルを評価する

評価は、モデルが適切に機能するかどうかを確認するプロセスです。 トレーニング時には使用しなかったデータを適切に予測できるかどうかが重要になります。 そのための方法の 1 つとしては、このチュートリアルで行ったように、データをトレーニング用のデータ セットとテスト用のデータ セットに分けます。 トレーニング用データでのモデルのトレーニングは完了しているので、テスト用データでモデルが適切に機能するかどうかを確認できます。

`Main` 関数に戻り、`Train()` メソッドの呼び出しの下に次のコードを追加します。

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate()` 関数はモデルを評価します。 その関数を `Train()` の下に作成します。 次のコードを追加します。

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

`TextLoader()` 関数を使用して、テスト用データを読み込みます。 `Evaluate()` メソッドに次のコードを追加します。

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

モデルを評価する次のコードを追加して、メトリックを生成します。

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

RMS は、回帰問題を評価するための 1 つのメトリックです。 RMS が低いほど優れたモデルになります。 `Evaluate()` 関数に次のコードを追加して、モデルの RMS を出力します。

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

RSquared は、回帰問題を評価するためのもう 1 つのメトリックです。 RSquared の値は 0 ～ 1 です。 1 に近づくほど優れたモデルになります。 `Evaluate()` 関数に次のコードを追加して、モデルの RSquared 値を出力します。

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>モデルを使用して予測を行う

次に、モデルが正しく機能しているかどうかを確認するためのテスト シナリオを格納するクラスを作成します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TestTrips.cs* に変更します。 次に、**[追加]** を選択します。
1. 次の例に示すように、静的になるようにクラスを変更します。

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

このチュートリアルでは、このクラス内の 1 つのテスト用の旅行を使用します。 このサンプルを試行するために、後で他のシナリオを追加できます。 `TestTrips` クラスに次のコードを追加します。

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

この旅行にかかった実際の運賃は 29.5 ですが、プレースホルダーとして 0 を使用します。 機械学習アルゴリズムが運賃を予測します。

`Main` 関数に次のコードを追加します。 このコードで `TestTrip` データを使用してモデルをテストします。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

プログラムを実行し、テスト ケースに対して予測されたタクシー運賃を確認します。

おめでとうございます!  これで、タクシー運賃を予測する機械学習モデルが構築されて、その正確性の評価とテストが完了しました。 このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) リポジトリで確認できます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習タスクを選択する
> * データを準備して理解する
> * 学習パイプラインを作成する
> * データを読み込んで変換する
> * 学習アルゴリズムを選択する
> * モデルをトレーニングする
> * モデルを評価する
> * モデルを使用して予測を行う

学習を続けてその他のサンプルを確認するには、GitHub リポジトリをご覧ください。
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub リポジトリ](https://github.com/dotnet/machinelearning/)

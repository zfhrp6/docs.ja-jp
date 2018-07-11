---
title: ML.NET を使用してニューヨークのタクシー運賃を予測する (回帰)
description: 回帰のシナリオで ML.NET を使用する方法について説明します。
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9706dad0a8e32651496e0404be4501c2c70e9d75
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948632"
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

* [Visual Studio 2017 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。

## <a name="understand-the-problem"></a>問題を把握する

この問題の中心となるのは、**ニューヨーク市のタクシー旅行の運賃の予測**です。 一見すると、単に乗車距離に依存すると思われるかもしれません。 しかし、ニューヨークのタクシー会社は追加の乗客数や現金でなくクレジット カードによる支払いなど、その他の要因によって請求額を変えます。

## <a name="select-the-appropriate-machine-learning-task"></a>適切な機械学習タスクを選択する

タクシー運賃を予測するには、最初に適切な機械学習タスクを選択します。 ここでは、データ セット内のその他の要因に基づいて実際の値 (価格を表す倍精度値) を予測しようとしています。 そのため、[**回帰**](../resources/glossary.md#regression)タスクを選択します。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 **[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「TaxiFarePrediction」と入力し、**[OK]** を選択します。

2. プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

3. **Microsoft.ML NuGet パッケージ**をインストールします。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、**[参照]** タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

## <a name="prepare-and-understand-the-data"></a>データを準備して理解する

1. [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) データ セットと [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) データ セットをダウンロードして、前の手順で作成済みの *Data* フォルダーに保存します。 これらのデータ セットを使用して、機械学習モデルをトレーニングし、モデルの正確度を評価します。 これらのデータ セットは、[NYC TLC Taxi Trip データ セット](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)から取得したものです。

2. **ソリューション エクスプローラー**で、各 \*.csv ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[常時]** に変更します。

3. **taxi-fare-train.csv** データ セットを開き、最初の行の列ヘッダーを確認します。 各列を確認してください。 データについて把握し、どの列が**特徴**で、どの列が**ラベル**であるかを確認します。

**ラベル**は、予測する列の識別子です。 識別された**特徴**は、ラベルを予測するために使用します。

提供されているデータ セットには、次の列が含まれます。

* **vendor_id:** タクシー会社の ID は特徴です。
* **rate_code:** タクシー旅行のレートの種類は特徴です。
* **passenger_count:** 旅行の乗客数は特徴です。
* **trip_time_in_secs:** 旅行の所要時間です。 旅行が終わる前に、旅行の運賃を予測したいと考えます。 その時点では、旅行の所要時間はわかりません。 したがって、旅行の所要時間は特徴ではなく、この列はモデルから除外します。
* **trip_distance:** 旅行距離は特徴です。
* **payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。
* **fare_amount:** 支払った合計タクシー運賃はラベルです。

## <a name="create-data-classes"></a>データ クラスを作成する

入力データと予測のためのクラスを作成します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TaxiTrip.cs* に変更します。 次に、**[追加]** を選択します。
1. 以下の `using` ディレクティブを新しいファイルに追加します。

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

既存のクラス定義を削除し、2 つのクラス `TaxiTrip` と `TaxiTripFarePrediction` を含む次のコードを *TaxiTrip.cs* ファイルに追加します。

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` は入力データ クラスであり、各データ セット列の定義が含まれています。 [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) 属性を使用して、データ セット内のソース列のインデックスを指定します。

`TaxiTripFarePrediction` クラスは、予測結果を表すために使用します。 このクラスには、`Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 属性が適用された 1 つの浮動小数点型 (`FareAmount`) フィールドが含まれています。 **Score** 列は ML.NET 内で特別な列です。 モデルは、この列に予測値を出力します。

## <a name="define-data-and-model-paths"></a>データおよびモデルのパスを定義する

*Program.cs* ファイルに戻り、データ セットを含むファイルと、モデルを保存するためのファイルへのパスを保持するための 3 つのフィールドを追加します。

* `_datapath` には、モデルのトレーニングに使用するデータ セットがあるファイルへのパスが含まれます。
* `_testdatapath` には、モデルの評価に使用するデータ セットがあるファイルへのパスが含まれます。
* `_modelpath` には、トレーニング済みモデルが格納されるファイルへのパスが含まれます。

`Main` メソッドのすぐ上に次のコードを追加して、それらのパスを指定します。

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

上記のコードをコンパイルするには、*Program.cs* ファイルの先頭に次の `using` ディレクティブを追加します。

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>学習パイプラインを作成する

以下の追加の `using` ディレクティブを、*Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

`Main` で、`Console.WriteLine("Hello World!")` を次のコードに置き換えます。

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` メソッドは、モデルをトレーニングします。 次のコードを使用して、`Main` の直下にそのメソッドを作成します。

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

学習パイプラインは、モデルのトレーニングに必要なすべてのデータとアルゴリズムを読み込みます。 `Train` メソッドに次のコードを追加します。

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>データを読み込んで変換する

学習パイプラインが実行する最初の手順は、トレーニング データ セットからデータを読み込むことです。 ここでは、トレーニング データ セットは、`_datapath` フィールドによってパスが定義されるテキスト ファイルに格納されます。 そのファイルには列名を含んだヘッダーがあるので、データの読み込み中に最初の行は無視されます。 ファイル内の列はコンマ (",") で区切られます。 `Train` メソッドに次のコードを追加します。

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

次の手順では、`TaxiTrip` クラス内で定義された名前によって列を参照します。

モデルのトレーニングおよび評価が行われる場合、**Label** 列内の値が予測される適切な値と見なされます。 タクシー旅行の運賃を予測したいので、`FareAmount` 列を **Label** 列にコピーします。 そのためには、<xref:Microsoft.ML.Transforms.ColumnCopier> を使用して、次のコードを追加します。

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

モデルをトレーニングするアルゴリズムには、**数値**の特徴が必要であるため、カテゴリ データ (`VendorId`、`RateCode`、および `PaymentType`) 値を数字に変換する必要があります。 そのためには、<xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer> (さまざまな数値キーの値をそれぞれ、各列内のさまざまな値に割り当てます) を使用し、次のコードを追加します。

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

データの準備の最後の手順では、<xref:Microsoft.ML.Transforms.ColumnConcatenator> 変換クラスを使用して、すべての特徴列を **Features** 列に結合します。 この手順は、ラーナーが **Features** 列からの特徴のみを処理する場合に必要です。 次のコードを追加します。

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

`TripTime` 列 (データ セット ファイル内の `trip_time_in_secs` 列に対応する) が含まれていないことに注意してください。 既に確認したとおり、この列は有効な予測特徴ではありません。

> [!NOTE]
> これらの手順を成功させるには、前述の指定した順序でパイプラインに追加する必要があります。

## <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

データをパイプラインに追加して正しい入力形式に変換したら、学習アルゴリズム (**ラーナー**) を選択します。 ラーナーはモデルをトレーニングします。 この問題に対しては**回帰タスク**を選択するので、<xref:Microsoft.ML.Trainers.FastTreeRegressor> ラーナー (ML.NET によって提供される回帰ラーナーの 1 つ) を追加します。

<xref:Microsoft.ML.Trainers.FastTreeRegressor> ラーナーは、勾配ブースティングを利用します。 勾配ブースティングは、回帰問題に対応する機械学習の手法です。 この手法では、それぞれの回帰ツリーを段階的に構築します。 また、定義済みの損失関数を使用して、各ステップの誤差を測定し、次の段階で修正します。 結果は予測モデルですが、実際は弱い予測モデルの集合です。 勾配ブースティングについて詳しくは、「[Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression)」(ブーストされたデシジョン ツリー回帰) を参照してください。

前の手順で追加したデータ処理コードの後にある `Train` メソッドに次のコードを追加します。

```csharp
pipeline.Add(new FastTreeRegressor());
```

前述のすべての手順は個々のステートメントとしてパイプラインに追加しましたが、C# には使いやすいコレクションの初期化構文があるため、パイプラインの作成と初期化が簡単になります。 次のコードを使用して、これまでに追加したコードを `Train` メソッドに置き換えます。

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>モデルをトレーニングする

最後の手順は、モデルのトレーニングです。 ここまで、パイプライン内の項目は何も実行されていません。 `pipeline.Train<TInput, TOutput>` メソッドは、`TInput` 型のインスタンスを取り込んで `TOutput` 型のインスタンスを出力するモデルを生成します。 `Train` メソッドに次のコードを追加します。

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

以上です。 これで機械学習モデルのトレーニングが終了し、ニューヨーク市のタクシー運賃を予測できるようになりました。 それでは、モデルの正確度について理解してから、モデルを使用してタクシー運賃の値を予測する方法について説明します。

### <a name="save-the-model"></a>モデルを保存する

次の手順に進む前に、`Train` メソッドの末尾に次のコードを追加して、モデルを .zip ファイルに保存します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

`model.WriteAsync` の呼び出しに `await` ステートメントを追加した場合は、`Train` メソッドをタスクを返す非同期メソッドに変更する必要があります。 次のコードに示すように、`Train` のシグネチャを変更します。

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

`Train` メソッドの戻り値の型を変更した場合は、次のコードに示すように、`Main` メソッドで `Train` を呼び出すコードに `await` を追加する必要があります。

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

`Main` メソッドで `await` を使用する場合は、`Main` メソッドに `async` 修飾子が必要です。このメソッドは `Task` を返す必要があります。

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

また、次の `using` ディレクティブをファイルの先頭に追加する必要もあります。

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

`async Main` メソッドは C# 7.1 に追加された機能であり、プロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。 そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。 **[OK]** ボタンを選択します。

## <a name="evaluate-the-model"></a>モデルを評価する

評価は、モデルがラベル値を適切に予測するかどうかを確認するプロセスです。 モデルのトレーニング時に使用しなかったデータを適切に予測できるかどうかが重要になります。 そのための方法の 1 つとしては、このチュートリアルで行ったように、データをトレーニング用のデータ セットとテスト用のデータ セットに分けます。 トレーニング用データでのモデルのトレーニングは完了しているので、テスト用データでモデルが適切に機能するかどうかを確認できます。

`Main` メソッドに戻り、`Train` メソッドの呼び出しの下に次のコードを追加します。

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` メソッドはモデルを評価します。 そのメソッドを作成するには、`Train` メソッドの下に次のコードを追加します。

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

次のコードを `Evaluate` メソッドに追加して、テスト データの読み込みを設定します。

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

次のコードを追加してモデルを評価し、評価メトリックを生成します。

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) は回帰モデルの評価メトリックの 1 つです。 RMS が低いほど、優れたモデルになります。 `Evaluate` メソッドに次のコードを追加することで、RMS 値を表示します。

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) は回帰モデルのもう 1 つの評価メトリックです。 RSquared は 0 から 1 までの値を取ります。 値が 1 に近づくほど、優れたモデルになります。 次のコードを `Evaluate` メソッドに追加して、RSquared 値を表示します。

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>モデルを使用して予測を行う

次に、モデルが正しく機能しているかどうかを確認するためのテスト シナリオを格納するクラスを作成します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。
1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TestTrips.cs* に変更します。 次に、**[追加]** を選択します。
1. 次の例に示すように、静的になるようにクラスを変更します。

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

このチュートリアルでは、このクラス内の 1 つのテスト用の旅行を使用します。 モデルを試行するために後で他のシナリオを追加できます。 `TestTrips` クラスに次のコードを追加します。

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

この旅行の実際の運賃は 29.5 です。 このモデルでは運賃が予測されるので、プレース ホルダーとして 0 を使用します。

指定した旅行の運賃を予測するには、*Program.cs* ファイルに戻り、次のコードを `Main` メソッドに追加します。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

プログラムを実行し、テスト ケースに対して予測されたタクシー運賃を確認します。

おめでとうございます!  これで、タクシー旅行運賃を予測する機械学習モデルが正常に構築され、その正確度が評価され、このモデルを使用した予測が行われました。 このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) リポジトリで確認できます。

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

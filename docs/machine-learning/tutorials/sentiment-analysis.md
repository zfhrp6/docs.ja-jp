---
title: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する
description: バイナリ分類のシナリオで ML.NET を使用する方法を学習して、センチメント予測をどのように使用して適切なアクションを実行するかを理解します。
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e6c9ae0eb91fcb570209ce25d4a18a4dcd104724
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2018
ms.locfileid: "34860711"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a>チュートリアル: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する

> [!NOTE]
> このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。 詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。

このサンプル チュートリアルでは、Visual Studio 2017 で ML.NET を使用して、C# を使用する .NET Core コンソール アプリケーションからセンチメント分類器を作成する方法を示 します。

このチュートリアルでは、次の作業を行う方法について説明します。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習タスクを選択する
> * データを準備する
> * 学習パイプラインを作成する
> * 分類器を読み込む
> * モデルをトレーニングする
> * 別のデータ セットを使用してモデルを評価する
> * モデルを使用してテスト データの結果を予測する

## <a name="sentiment-analysis-sample-overview"></a>センチメント分析のサンプルの概要

このサンプルは ML.NET を使用するコンソール アプリケーションであり、センチメントを分類して肯定的か否定的かを予測するモデルをトレーニングします。 また、高品質な分析のために、2 番目のデータ セットを使用してモデルを評価します。 センチメントのデータ セットは、WikiDetox プロジェクトからのものです。

## <a name="prerequisites"></a>必須コンポーネント

* ".NET Core クロスプラットフォームの開発" ワークロードがインストールされた [Visual Studio 2017 15.6 以降](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

* [Wikipedia detox line data タブ区切りファイル (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)。
* [Wikipedia detox line test タブ区切りファイル (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv)。

## <a name="machine-learning-workflow"></a>機械学習ワークフロー

このチュートリアルでは、プロセスを順序立てて進められるようにする機械学習ワークフローに従います。

このワークフローには次のフェーズがあります。

1. **問題を把握する**
2. **データを取り込む**
3. **データの前処理とフィーチャー エンジニアリング**
4. **モデルをトレーニングおよび予測する**
5. **モデルを評価する**
6. **モデルの運用化**

### <a name="understand-the-problem"></a>問題を把握する

まず、問題を把握して、モデルのビルドおよびトレーニングに使用できるパーツに分ける必要があります。 問題を分けることで、結果の予測および評価ができるようになります。

このチュートリアルでの問題は、書き込まれた Web サイト コメントのセンチメントを解釈して適切なアクションを実行することです。

この問題は、モデルのトレーニングに使用するセンチメント テキストおよびセンチメント値と、評価して運用に使用することができる予測されたセンチメント値に分けることができます。

次に、センチメントを**決定**する必要があります。これは機械学習タスクを選択するときに役立ちます。

## <a name="select-the-appropriate-machine-learning-task"></a>適切な機械学習タスクを選択する

この問題に関してわかっていることは次のとおりです。

トレーニング データである Web サイト コメントは、肯定的か否定的 (**センチメント**) のいずれかとなります。
次の例のような、新しい Web サイト コメントの**センチメント**が肯定的か否定的かを予測します。

* Wikipedia に無意味な記述を追加するのはやめてください。
* 彼は最高です。記事ではそのことを記述するべきです。

このシナリオには、分類機械学習タスクが適しています。

### <a name="about-the-classification-task"></a>分類タスクについて

分類とは、データを使用して項目またはデータ行のカテゴリ、型、クラスを**判断**する機械学習タスクです。 分類はたとえば、次のような目的に使用できます。

* センチメントが肯定的か否定的かを判断する。
* 電子メールをスパム、迷惑メール、正常なメールに分類する。
* 患者の検体が癌性かどうかを判断する。
* 顧客を販売キャンペーンへの反応性で分類する。

多くの場合、分類タスクは次のいずれかの種類です。

* バイナリ: A か B のいずれかである。
* 多クラス: 1 つのモデルを使用して予測できるカテゴリが多数ある。

## <a name="create-a-console-application"></a>コンソール アプリケーションを作成する

1. Visual Studio 2017 を開きます。 **[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。 [*新しいプロジェクト**] ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。 次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。 **[名前]** テキスト ボックスに「SentimentAnalysis」と入力し、**[OK]** を選択します。

2. プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。

    **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。 「Data」と入力して Enter キーを押します。

3. **Microsoft.ML NuGet パッケージ**をインストールします。

    ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。 [パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。 **[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。

### <a name="prepare-your-data"></a>データを準備する

1. [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) データ セットと [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) データ セットをダウンロードして、作成済みの *Data* フォルダーに保存します。 1 番目のデータ セットでは機械学習モデルをトレーニングし、2 番目のデータ セットはモデルの精度を評価するために使用します。

2. ソリューション エクスプローラーで、各 \*.tsv ファイルを右クリックし、**[プロパティ]** を選択します。 **[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[常時]** に変更します。

### <a name="create-classes-and-define-paths"></a>クラスを作成してパスを定義する

次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

最近ダウンロードしたファイルのパスを保持する 3 つのグローバル変数を作成する必要があります。

* `_dataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。
* `_testDataPath` には、モデルの評価に使用するデータ セットのパスが含まれます。
* `_modelPath` には、トレーニング済みのモデルを保存するパスが含まれます。

`Main` メソッドのすぐ上にある行に次のコードを追加して、最近ダウンロードしたファイルを指定します。

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

入力データと予測のために、いくつかのクラスを作成する必要があります。 プロジェクトに新しいクラスを追加します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。

1. **[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。 次に、**[追加]** を選択します。

    コード エディターで *SentimentData.cs* ファイルが開きます。 *SentimentData.cs* の先頭に次の `using` ステートメントを 追加します。

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

既存のクラス定義を削除し、`SentimentData` と `SentimentPrediction` の 2 つのクラスを含む次のコードを *SentimentData.cs* ファイルに追加します。

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

`SentimentData` は入力データ セット クラスで、肯定的か否定的のいずれかのセンチメント値を持つ `float` (`Sentiment`) と、コメントの文字列 (`SentimentText`) を含みます。 どちらのフィールドにも `Column` 属性が添付されています。 この属性はデータ ファイル内での各フィールドの順序と、どちらが `Label` フィールドであるかを示しています。 `SentimentPrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。 これは、1 つのブール値 (`Sentiment`) と、`PredictedLabel` `ColumnName` 属性を持ちます。 `Label` はモデルを作成してトレーニングするために使用され、2 番目のデータ セットでもモデルを評価するために使用されます。 `PredictedLabel` は予測と評価の際に使用されます。 評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。

*Program.cs* ファイルで、`Main` メソッド のシグネチャを、次の例のように `void` を `async Task` で置き換えて変更します。

```csharp
static async Task Main(string[] args) 
{

}
```

後でモデルを zip ファイルに保存し、外部タスクが完了するまでプログラムを待機させる必要があるため、`async` は戻り値の型 <xref:System.Threading.Tasks.Task> を指定して `Main` に追加します。

> [!NOTE]
> *async main* メソッドにより、`Main` メソッドで `await` を使用できます。 詳細については、C# プログラミング ガイドの [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) に関するトピックを参照してください。

`Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

`Train` メソッドは次のタスクを実行します。

* データを読み込む (取り込む)。
* データの前処理と特徴付けを行う。
* モデルをトレーニングする。
* テスト データに基づいてセンチメントを予測する。

`Main` メソッドの直後に、次のコードを使用して `Train` メソッドを作成します。

```csharp
public static PredictionModel<SentimentData, SentimentPrediction> Train()
{

}
```

## <a name="ingest-the-data"></a>データを取り込む

<xref:Microsoft.ML.LearningPipeline> の新しいインスタンスを初期化します。ここに、データの読み込み、データの処理/特徴付け、およびモデルを含めます。 `Train` メソッドの最初の行として、次のコードを追加します。

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<xref:Microsoft.ML.TextLoader%601> オブジェクトはパイプラインの最初の部分であり、トレーニング ファイルのデータを読み込みます。

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a>データの前処理とフィーチャー エンジニアリング

データの前処理とクリーニングは、機械学習でデータ セットを効果的に使用する前に発生する重要なタスクです。 多くの場合、生データはノイズが多くて信頼性が低く、値が欠落している可能性もあります。 これらのモデル化タスクを行わずにデータを使用すると、誤解を招く結果が生じるおそれがあります。 ML.NET の変換パイプラインを使用すると、トレーニングまたはテストの前にデータに適用するカスタム変換セットを作成できます。 この変換の主な目的は、データの特徴付けです。 変換パイプラインの利点は、変換パイプラインの定義後に、パイプラインを保存してテスト データに適用できることです。

`SentimentText` 列を機械学習アルゴリズムで使用される `Features` という[数値ベクトル](../resources/glossary.md#numerical-feature-vector)に変換するために、<xref:Microsoft.ML.Transforms.TextFeaturizer> を適用します。 これが前処理/特徴付けのステップです。 ML.NET に用意されているその他のコンポーネントを使用すると、モデルでより良い結果が得られます。 パイプラインに、次のコード行として `TextFeaturizer` を追加します。

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a>学習アルゴリズムを選択する

<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> オブジェクトは、このパイプラインで使用するデシジョン ツリーの学習器です。 特徴付けのステップと同様に、ML.NET に用意されているさまざまな学習器を試してパラメーターを変更すると、異なる結果が生成されます。 チューニングのために、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs> などの[ハイパーパラメーター](../resources/glossary.md#hyperparameter)を設定できます。 これらのハイパーパラメーターは、モデルが何らかの影響を受ける前に設定され、モデルに固有です。 これはパフォーマンスのためにデシジョン ツリーのチューニングに使用されるため、値を大きくするとパフォーマンスに悪影響を及ぼす可能性があります。

`Train` メソッドに次のコードを追加します。

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a>モデルをトレーニングする

読み込まれて変換されたデータ セットに基づいて、モデル <xref:Microsoft.ML.PredictionModel%602> をトレーニングします。 `pipeline.Train<SentimentData, SentimentPrediction>()` は、パイプラインをトレーニングします (データを読み込み、特徴付け器と学習器をトレーニングします)。 これが行われるまで、実験は実行されません。

`Train` メソッドに次のコードを追加します。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a>評価に使用する、トレーニングされたモデルを保存して返す

この時点で、既存または新規のどの .NET アプリケーションにも統合できるモデルができました。 モデルを返す前に .zip ファイルに保存するには、`Train` 内の次の行に次のコードを追加します。

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

`Train` メソッドの最後で、モデルを返します。

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a>モデルを評価する

これでモデルの作成とトレーニングが完了したので、品質保証と検証のために、別のデータ セットを使用してモデルを評価します。 `Evaluate` メソッドでは、`Train` で作成されたモデルが渡されて評価されます。 `Train` の直後に、次のコードに示すように `Evaluate` メソッドを作成します。

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Evaluate` メソッドは次のタスクを実行します。

* テスト データ セットを読み込む。
* バイナリ評価器を作成する。
* モデルを評価し、メトリックを作成する。
* メトリックを表示する。

`Train` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<xref:Microsoft.ML.TextLoader%601> クラスは、同じスキーマを持つ新しいテスト データ セットを読み込みます。 このデータ セットを品質チェックとして使用して、モデルを評価できます。 `Evaluate` メソッドに次のコードを追加します。

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<xref:Microsoft.ML.Models.BinaryClassificationEvaluator> オブジェクトは、指定されたデータ セットを使用して `PredictionModel` の品質メトリックを計算します。 それらのメトリックを表示するには、次のコードを使用して、評価器を `Evaluate` メソッド内の次の行として追加します。

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<xref:Microsoft.ML.Models.BinaryClassificationMetrics> には、バイナリ分類評価器によって計算されるメトリック全体が含まれます。 これらを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。 次のコードを追加します。

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a>モデル検証のためのメトリックを表示する

次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a>モデルを使用してテスト データの結果を予測する

`Evaluate` メソッドの直後に、次のコードを使用して `Predict` メソッドを作成します。

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

`Predict` メソッドは次のタスクを実行します。

* テスト データを作成する。
* テスト データに基づいてセンチメントを予測する。
* テスト データと予測をレポート用に結合する。
* 予測された結果を表示する。

`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

`Predict` メソッドでトレーニングされるモデルの予測をテストするために、いくつかのコメントを追加します。

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

モデルは既にあるので、それを利用して、<xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> メソッドでコメント データのセンチメントが肯定的か否定的かを予測できます。 予測を取得するには、新しいデータに対して `Predict` を使用します。 入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。 トレーニングと予測の間は、パイプラインが同期されます。 予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a>モデルの運用化: 予測

結果を共有し、それに応じたアクションを実行するために、`SentimentText` および対応するセンチメント予測を表示します。 これは運用化と呼ばれ、返されたデータを運用ポリシーとして使用します。 次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果のヘッダーを作成します。

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

予測された結果を表示する前に、元のコメントとその予測されたセンチメントが一緒に表示されるように、センチメントと予測を結合します。 次のコードでは <xref:System.Linq.Enumerable.Zip%2A> メソッドを使用してそれを行うため、そのコードを次に追加します。

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

これで `SentimentText` と `Sentiment` が 1 つのクラスに結合されたので、<xref:System.Console.WriteLine?displayProperty=nameWithType> メソッドを使用して結果を表示できます。

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

推定されたタプル要素名は C# 7.1 の新機能であり、このプロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。
そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。 **[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。 ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。 **[OK]** ボタンを選択します。

## <a name="results"></a>結果

結果は以下のようになるはずです。 パイプラインが処理されると、メッセージが表示されます。 警告または処理メッセージが表示されることがありますが、 わかりやすくするために、それらは次の結果から削除してあります。

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

おめでとうございます!  これで、メッセージのセンチメントを分類および予測するための機械学習モデルをビルドできました。 このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、次の作業を行う方法を学びました。
> [!div class="checklist"]
> * 問題を把握する
> * 適切な機械学習タスクを選択する
> * データを準備する
> * 学習パイプラインを作成する
> * 分類器を読み込む
> * モデルをトレーニングする
> * 別のデータ セットを使用してモデルを評価する
> * モデルを使用してテスト データの結果を予測する

さらに詳しく学習するには、次のチュートリアルに進んでください。
> [!div class="nextstepaction"]
> [タクシー代予測](taxi-fare.md)

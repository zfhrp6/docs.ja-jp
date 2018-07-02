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
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="a3244-103">チュートリアル: センチメント分析のバイナリ分類のシナリオで ML.NET を使用する</span><span class="sxs-lookup"><span data-stu-id="a3244-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="a3244-104">このトピックは現在プレビュー中の ML.NET について述べており、内容が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="a3244-105">詳細については、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3244-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="a3244-106">このサンプル チュートリアルでは、Visual Studio 2017 で ML.NET を使用して、C# を使用する .NET Core コンソール アプリケーションからセンチメント分類器を作成する方法を示 します。</span><span class="sxs-lookup"><span data-stu-id="a3244-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="a3244-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3244-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a3244-108">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="a3244-108">Understand the problem</span></span>
> * <span data-ttu-id="a3244-109">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="a3244-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="a3244-110">データを準備する</span><span class="sxs-lookup"><span data-stu-id="a3244-110">Prepare your data</span></span>
> * <span data-ttu-id="a3244-111">学習パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="a3244-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="a3244-112">分類器を読み込む</span><span class="sxs-lookup"><span data-stu-id="a3244-112">Load a classifier</span></span>
> * <span data-ttu-id="a3244-113">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="a3244-113">Train the model</span></span>
> * <span data-ttu-id="a3244-114">別のデータ セットを使用してモデルを評価する</span><span class="sxs-lookup"><span data-stu-id="a3244-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="a3244-115">モデルを使用してテスト データの結果を予測する</span><span class="sxs-lookup"><span data-stu-id="a3244-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="a3244-116">センチメント分析のサンプルの概要</span><span class="sxs-lookup"><span data-stu-id="a3244-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="a3244-117">このサンプルは ML.NET を使用するコンソール アプリケーションであり、センチメントを分類して肯定的か否定的かを予測するモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="a3244-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="a3244-118">また、高品質な分析のために、2 番目のデータ セットを使用してモデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="a3244-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="a3244-119">センチメントのデータ セットは、WikiDetox プロジェクトからのものです。</span><span class="sxs-lookup"><span data-stu-id="a3244-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a3244-120">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a3244-120">Prerequisites</span></span>

* <span data-ttu-id="a3244-121">".NET Core クロスプラットフォームの開発" ワークロードがインストールされた [Visual Studio 2017 15.6 以降](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="a3244-121">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="a3244-122">[Wikipedia detox line data タブ区切りファイル (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)。</span><span class="sxs-lookup"><span data-stu-id="a3244-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="a3244-123">[Wikipedia detox line test タブ区切りファイル (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv)。</span><span class="sxs-lookup"><span data-stu-id="a3244-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="a3244-124">機械学習ワークフロー</span><span class="sxs-lookup"><span data-stu-id="a3244-124">Machine learning workflow</span></span>

<span data-ttu-id="a3244-125">このチュートリアルでは、プロセスを順序立てて進められるようにする機械学習ワークフローに従います。</span><span class="sxs-lookup"><span data-stu-id="a3244-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="a3244-126">このワークフローには次のフェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="a3244-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="a3244-127">**問題を把握する**</span><span class="sxs-lookup"><span data-stu-id="a3244-127">**Understand the problem**</span></span>
2. <span data-ttu-id="a3244-128">**データを取り込む**</span><span class="sxs-lookup"><span data-stu-id="a3244-128">**Ingest the data**</span></span>
3. <span data-ttu-id="a3244-129">**データの前処理とフィーチャー エンジニアリング**</span><span class="sxs-lookup"><span data-stu-id="a3244-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="a3244-130">**モデルをトレーニングおよび予測する**</span><span class="sxs-lookup"><span data-stu-id="a3244-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="a3244-131">**モデルを評価する**</span><span class="sxs-lookup"><span data-stu-id="a3244-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="a3244-132">**モデルの運用化**</span><span class="sxs-lookup"><span data-stu-id="a3244-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="a3244-133">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="a3244-133">Understand the problem</span></span>

<span data-ttu-id="a3244-134">まず、問題を把握して、モデルのビルドおよびトレーニングに使用できるパーツに分ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="a3244-135">問題を分けることで、結果の予測および評価ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="a3244-135">Breaking the problem down you to predict and evaluate the results.</span></span>

<span data-ttu-id="a3244-136">このチュートリアルでの問題は、書き込まれた Web サイト コメントのセンチメントを解釈して適切なアクションを実行することです。</span><span class="sxs-lookup"><span data-stu-id="a3244-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="a3244-137">この問題は、モデルのトレーニングに使用するセンチメント テキストおよびセンチメント値と、評価して運用に使用することができる予測されたセンチメント値に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="a3244-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="a3244-138">次に、センチメントを**決定**する必要があります。これは機械学習タスクを選択するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a3244-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="a3244-139">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="a3244-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="a3244-140">この問題に関してわかっていることは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a3244-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="a3244-141">トレーニング データである Web サイト コメントは、肯定的か否定的 (**センチメント**) のいずれかとなります。</span><span class="sxs-lookup"><span data-stu-id="a3244-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="a3244-142">次の例のような、新しい Web サイト コメントの**センチメント**が肯定的か否定的かを予測します。</span><span class="sxs-lookup"><span data-stu-id="a3244-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="a3244-143">Wikipedia に無意味な記述を追加するのはやめてください。</span><span class="sxs-lookup"><span data-stu-id="a3244-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="a3244-144">彼は最高です。記事ではそのことを記述するべきです。</span><span class="sxs-lookup"><span data-stu-id="a3244-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="a3244-145">このシナリオには、分類機械学習タスクが適しています。</span><span class="sxs-lookup"><span data-stu-id="a3244-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="a3244-146">分類タスクについて</span><span class="sxs-lookup"><span data-stu-id="a3244-146">About the classification task</span></span>

<span data-ttu-id="a3244-147">分類とは、データを使用して項目またはデータ行のカテゴリ、型、クラスを**判断**する機械学習タスクです。</span><span class="sxs-lookup"><span data-stu-id="a3244-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="a3244-148">分類はたとえば、次のような目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="a3244-149">センチメントが肯定的か否定的かを判断する。</span><span class="sxs-lookup"><span data-stu-id="a3244-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="a3244-150">電子メールをスパム、迷惑メール、正常なメールに分類する。</span><span class="sxs-lookup"><span data-stu-id="a3244-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="a3244-151">患者の検体が癌性かどうかを判断する。</span><span class="sxs-lookup"><span data-stu-id="a3244-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="a3244-152">顧客を販売キャンペーンへの反応性で分類する。</span><span class="sxs-lookup"><span data-stu-id="a3244-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="a3244-153">多くの場合、分類タスクは次のいずれかの種類です。</span><span class="sxs-lookup"><span data-stu-id="a3244-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="a3244-154">バイナリ: A か B のいずれかである。</span><span class="sxs-lookup"><span data-stu-id="a3244-154">Binary: either A or B.</span></span>
* <span data-ttu-id="a3244-155">多クラス: 1 つのモデルを使用して予測できるカテゴリが多数ある。</span><span class="sxs-lookup"><span data-stu-id="a3244-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a3244-156">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a3244-156">Create a console application</span></span>

1. <span data-ttu-id="a3244-157">Visual Studio 2017 を開きます。</span><span class="sxs-lookup"><span data-stu-id="a3244-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="a3244-158">**[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="a3244-159">[*新しいプロジェクト**] ダイアログで、**[Visual C#]*\* ノードを選択し、**[.NET Core]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-159">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="a3244-160">次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="a3244-161">**[名前]** テキスト ボックスに「SentimentAnalysis」と入力し、**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="a3244-162">プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="a3244-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="a3244-163">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="a3244-164">「Data」と入力して Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a3244-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="a3244-165">**Microsoft.ML NuGet パッケージ**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a3244-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="a3244-166">ソリューション エクスプローラーで、プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a3244-167">[パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="a3244-168">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="a3244-169">データを準備する</span><span class="sxs-lookup"><span data-stu-id="a3244-169">Prepare your data</span></span>

1. <span data-ttu-id="a3244-170">[WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) データ セットと [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) データ セットをダウンロードして、作成済みの *Data* フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="a3244-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="a3244-171">1 番目のデータ セットでは機械学習モデルをトレーニングし、2 番目のデータ セットはモデルの精度を評価するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a3244-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="a3244-172">ソリューション エクスプローラーで、各 \*.tsv ファイルを右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="a3244-173">**[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[常時]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="a3244-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a3244-174">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="a3244-174">Create classes and define paths</span></span>

<span data-ttu-id="a3244-175">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="a3244-176">最近ダウンロードしたファイルのパスを保持する 3 つのグローバル変数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-176">You need to create three global variables to hold the path to the recently downloaded files:</span></span>

* <span data-ttu-id="a3244-177">`_dataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3244-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="a3244-178">`_testDataPath` には、モデルの評価に使用するデータ セットのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3244-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="a3244-179">`_modelPath` には、トレーニング済みのモデルを保存するパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3244-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="a3244-180">`Main` メソッドのすぐ上にある行に次のコードを追加して、最近ダウンロードしたファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a3244-180">Add the following code to the line right above the `Main` method to specify the recently downloaded files:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="a3244-181">入力データと予測のために、いくつかのクラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="a3244-182">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="a3244-183">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="a3244-184">**[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *SentimentData.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="a3244-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="a3244-185">次に、**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="a3244-186">コード エディターで *SentimentData.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="a3244-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="a3244-187">*SentimentData.cs* の先頭に次の `using` ステートメントを 追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="a3244-188">既存のクラス定義を削除し、`SentimentData` と `SentimentPrediction` の 2 つのクラスを含む次のコードを *SentimentData.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="a3244-189">`SentimentData` は入力データ セット クラスで、肯定的か否定的のいずれかのセンチメント値を持つ `float` (`Sentiment`) と、コメントの文字列 (`SentimentText`) を含みます。</span><span class="sxs-lookup"><span data-stu-id="a3244-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="a3244-190">どちらのフィールドにも `Column` 属性が添付されています。</span><span class="sxs-lookup"><span data-stu-id="a3244-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="a3244-191">この属性はデータ ファイル内での各フィールドの順序と、どちらが `Label` フィールドであるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="a3244-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="a3244-192">`SentimentPrediction` は、モデルがトレーニングされた後に、予測に使用されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="a3244-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="a3244-193">これは、1 つのブール値 (`Sentiment`) と、`PredictedLabel` `ColumnName` 属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="a3244-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="a3244-194">`Label` はモデルを作成してトレーニングするために使用され、2 番目のデータ セットでもモデルを評価するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="a3244-195">`PredictedLabel` は予測と評価の際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="a3244-196">評価では、トレーニング データを含む入力、予測された値、およびモデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="a3244-197">*Program.cs* ファイルで、`Main` メソッド のシグネチャを、次の例のように `void` を `async Task` で置き換えて変更します。</span><span class="sxs-lookup"><span data-stu-id="a3244-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="a3244-198">後でモデルを zip ファイルに保存し、外部タスクが完了するまでプログラムを待機させる必要があるため、`async` は戻り値の型 <xref:System.Threading.Tasks.Task> を指定して `Main` に追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="a3244-199">*async main* メソッドにより、`Main` メソッドで `await` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="a3244-200">詳細については、C# プログラミング ガイドの [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3244-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="a3244-201">`Main` メソッドの `Console.WriteLine("Hello World!")` 行を、次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a3244-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="a3244-202">`Train` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3244-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="a3244-203">データを読み込む (取り込む)。</span><span class="sxs-lookup"><span data-stu-id="a3244-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="a3244-204">データの前処理と特徴付けを行う。</span><span class="sxs-lookup"><span data-stu-id="a3244-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="a3244-205">モデルをトレーニングする。</span><span class="sxs-lookup"><span data-stu-id="a3244-205">Trains the model.</span></span>
* <span data-ttu-id="a3244-206">テスト データに基づいてセンチメントを予測する。</span><span class="sxs-lookup"><span data-stu-id="a3244-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="a3244-207">`Main` メソッドの直後に、次のコードを使用して `Train` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3244-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static PredictionModel<SentimentData, SentimentPrediction> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="a3244-208">データを取り込む</span><span class="sxs-lookup"><span data-stu-id="a3244-208">Ingest the data</span></span>

<span data-ttu-id="a3244-209"><xref:Microsoft.ML.LearningPipeline> の新しいインスタンスを初期化します。ここに、データの読み込み、データの処理/特徴付け、およびモデルを含めます。</span><span class="sxs-lookup"><span data-stu-id="a3244-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="a3244-210">`Train` メソッドの最初の行として、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="a3244-211"><xref:Microsoft.ML.TextLoader%601> オブジェクトはパイプラインの最初の部分であり、トレーニング ファイルのデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a3244-211">The <xref:Microsoft.ML.TextLoader%601> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="a3244-212">データの前処理とフィーチャー エンジニアリング</span><span class="sxs-lookup"><span data-stu-id="a3244-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="a3244-213">データの前処理とクリーニングは、機械学習でデータ セットを効果的に使用する前に発生する重要なタスクです。</span><span class="sxs-lookup"><span data-stu-id="a3244-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="a3244-214">多くの場合、生データはノイズが多くて信頼性が低く、値が欠落している可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="a3244-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="a3244-215">これらのモデル化タスクを行わずにデータを使用すると、誤解を招く結果が生じるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="a3244-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="a3244-216">ML.NET の変換パイプラインを使用すると、トレーニングまたはテストの前にデータに適用するカスタム変換セットを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="a3244-217">この変換の主な目的は、データの特徴付けです。</span><span class="sxs-lookup"><span data-stu-id="a3244-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="a3244-218">変換パイプラインの利点は、変換パイプラインの定義後に、パイプラインを保存してテスト データに適用できることです。</span><span class="sxs-lookup"><span data-stu-id="a3244-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="a3244-219">`SentimentText` 列を機械学習アルゴリズムで使用される `Features` という[数値ベクトル](../resources/glossary.md#numerical-feature-vector)に変換するために、<xref:Microsoft.ML.Transforms.TextFeaturizer> を適用します。</span><span class="sxs-lookup"><span data-stu-id="a3244-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="a3244-220">これが前処理/特徴付けのステップです。</span><span class="sxs-lookup"><span data-stu-id="a3244-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="a3244-221">ML.NET に用意されているその他のコンポーネントを使用すると、モデルでより良い結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="a3244-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="a3244-222">パイプラインに、次のコード行として `TextFeaturizer` を追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="a3244-223">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="a3244-223">Choose a learning algorithm</span></span>

<span data-ttu-id="a3244-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> オブジェクトは、このパイプラインで使用するデシジョン ツリーの学習器です。</span><span class="sxs-lookup"><span data-stu-id="a3244-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="a3244-225">特徴付けのステップと同様に、ML.NET に用意されているさまざまな学習器を試してパラメーターを変更すると、異なる結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="a3244-226">チューニングのために、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs> などの[ハイパーパラメーター](../resources/glossary.md#hyperparameter)を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="a3244-227">これらのハイパーパラメーターは、モデルが何らかの影響を受ける前に設定され、モデルに固有です。</span><span class="sxs-lookup"><span data-stu-id="a3244-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="a3244-228">これはパフォーマンスのためにデシジョン ツリーのチューニングに使用されるため、値を大きくするとパフォーマンスに悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="a3244-229">`Train` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="a3244-230">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="a3244-230">Train the model</span></span>

<span data-ttu-id="a3244-231">読み込まれて変換されたデータ セットに基づいて、モデル <xref:Microsoft.ML.PredictionModel%602> をトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="a3244-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="a3244-232">`pipeline.Train<SentimentData, SentimentPrediction>()` は、パイプラインをトレーニングします (データを読み込み、特徴付け器と学習器をトレーニングします)。</span><span class="sxs-lookup"><span data-stu-id="a3244-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="a3244-233">これが行われるまで、実験は実行されません。</span><span class="sxs-lookup"><span data-stu-id="a3244-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="a3244-234">`Train` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="a3244-235">評価に使用する、トレーニングされたモデルを保存して返す</span><span class="sxs-lookup"><span data-stu-id="a3244-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="a3244-236">この時点で、既存または新規のどの .NET アプリケーションにも統合できるモデルができました。</span><span class="sxs-lookup"><span data-stu-id="a3244-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="a3244-237">モデルを返す前に .zip ファイルに保存するには、`Train` 内の次の行に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="a3244-238">`Train` メソッドの最後で、モデルを返します。</span><span class="sxs-lookup"><span data-stu-id="a3244-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="a3244-239">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="a3244-239">Evaluate the model</span></span>

<span data-ttu-id="a3244-240">これでモデルの作成とトレーニングが完了したので、品質保証と検証のために、別のデータ セットを使用してモデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="a3244-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="a3244-241">`Evaluate` メソッドでは、`Train` で作成されたモデルが渡されて評価されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="a3244-242">`Train` の直後に、次のコードに示すように `Evaluate` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3244-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="a3244-243">`Evaluate` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3244-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="a3244-244">テスト データ セットを読み込む。</span><span class="sxs-lookup"><span data-stu-id="a3244-244">Loads the test dataset.</span></span>
* <span data-ttu-id="a3244-245">バイナリ評価器を作成する。</span><span class="sxs-lookup"><span data-stu-id="a3244-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="a3244-246">モデルを評価し、メトリックを作成する。</span><span class="sxs-lookup"><span data-stu-id="a3244-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="a3244-247">メトリックを表示する。</span><span class="sxs-lookup"><span data-stu-id="a3244-247">Displays the metrics.</span></span>

<span data-ttu-id="a3244-248">`Train` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="a3244-249"><xref:Microsoft.ML.TextLoader%601> クラスは、同じスキーマを持つ新しいテスト データ セットを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a3244-249">The <xref:Microsoft.ML.TextLoader%601> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="a3244-250">このデータ セットを品質チェックとして使用して、モデルを評価できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="a3244-251">`Evaluate` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="a3244-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> オブジェクトは、指定されたデータ セットを使用して `PredictionModel` の品質メトリックを計算します。</span><span class="sxs-lookup"><span data-stu-id="a3244-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="a3244-253">それらのメトリックを表示するには、次のコードを使用して、評価器を `Evaluate` メソッド内の次の行として追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="a3244-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> には、バイナリ分類評価器によって計算されるメトリック全体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a3244-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="a3244-255">これらを表示してモデルの品質を判定するには、最初にメトリックを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="a3244-256">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="a3244-257">モデル検証のためのメトリックを表示する</span><span class="sxs-lookup"><span data-stu-id="a3244-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="a3244-258">次のコードを使用してメトリックを表示し、結果を共有し、それに対してアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3244-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="a3244-259">モデルを使用してテスト データの結果を予測する</span><span class="sxs-lookup"><span data-stu-id="a3244-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="a3244-260">`Evaluate` メソッドの直後に、次のコードを使用して `Predict` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3244-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="a3244-261">`Predict` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3244-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="a3244-262">テスト データを作成する。</span><span class="sxs-lookup"><span data-stu-id="a3244-262">Creates test data.</span></span>
* <span data-ttu-id="a3244-263">テスト データに基づいてセンチメントを予測する。</span><span class="sxs-lookup"><span data-stu-id="a3244-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="a3244-264">テスト データと予測をレポート用に結合する。</span><span class="sxs-lookup"><span data-stu-id="a3244-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="a3244-265">予測された結果を表示する。</span><span class="sxs-lookup"><span data-stu-id="a3244-265">Displays the predicted results.</span></span>

<span data-ttu-id="a3244-266">`Evaluate` メソッドの呼び出しのすぐ下に、次のコードを使用して、`Main` メソッドからの新しいメソッドの呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="a3244-267">`Predict` メソッドでトレーニングされるモデルの予測をテストするために、いくつかのコメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="a3244-268">モデルは既にあるので、それを利用して、<xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> メソッドでコメント データのセンチメントが肯定的か否定的かを予測できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a3244-269">予測を取得するには、新しいデータに対して `Predict` を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3244-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="a3244-270">入力データは文字列であり、モデルには、特徴付けが含まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a3244-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="a3244-271">トレーニングと予測の間は、パイプラインが同期されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="a3244-272">予測のために前処理/特徴付けのコードを特別に記述する必要はなく、同じ API によってバッチと 1 回限りの予測の両方が処理されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="a3244-273">モデルの運用化: 予測</span><span class="sxs-lookup"><span data-stu-id="a3244-273">Model operationalization: prediction</span></span>

<span data-ttu-id="a3244-274">結果を共有し、それに応じたアクションを実行するために、`SentimentText` および対応するセンチメント予測を表示します。</span><span class="sxs-lookup"><span data-stu-id="a3244-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="a3244-275">これは運用化と呼ばれ、返されたデータを運用ポリシーとして使用します。</span><span class="sxs-lookup"><span data-stu-id="a3244-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="a3244-276">次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して、結果のヘッダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3244-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="a3244-277">予測された結果を表示する前に、元のコメントとその予測されたセンチメントが一緒に表示されるように、センチメントと予測を結合します。</span><span class="sxs-lookup"><span data-stu-id="a3244-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="a3244-278">次のコードでは <xref:System.Linq.Enumerable.Zip%2A> メソッドを使用してそれを行うため、そのコードを次に追加します。</span><span class="sxs-lookup"><span data-stu-id="a3244-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="a3244-279">これで `SentimentText` と `Sentiment` が 1 つのクラスに結合されたので、<xref:System.Console.WriteLine?displayProperty=nameWithType> メソッドを使用して結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="a3244-280">推定されたタプル要素名は C# 7.1 の新機能であり、このプロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3244-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="a3244-281">そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="a3244-282">**[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="a3244-283">ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="a3244-284">**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="a3244-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="a3244-285">結果</span><span class="sxs-lookup"><span data-stu-id="a3244-285">Results</span></span>

<span data-ttu-id="a3244-286">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="a3244-286">Your results should be similar to the following.</span></span> <span data-ttu-id="a3244-287">パイプラインが処理されると、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3244-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="a3244-288">警告または処理メッセージが表示されることがありますが、</span><span class="sxs-lookup"><span data-stu-id="a3244-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a3244-289">わかりやすくするために、それらは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="a3244-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="a3244-290">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="a3244-290">Congratulations!</span></span> <span data-ttu-id="a3244-291">これで、メッセージのセンチメントを分類および予測するための機械学習モデルをビルドできました。</span><span class="sxs-lookup"><span data-stu-id="a3244-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="a3244-292">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="a3244-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a3244-293">次の手順</span><span class="sxs-lookup"><span data-stu-id="a3244-293">Next steps</span></span>

<span data-ttu-id="a3244-294">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="a3244-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a3244-295">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="a3244-295">Understand the problem</span></span>
> * <span data-ttu-id="a3244-296">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="a3244-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="a3244-297">データを準備する</span><span class="sxs-lookup"><span data-stu-id="a3244-297">Prepare your data</span></span>
> * <span data-ttu-id="a3244-298">学習パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="a3244-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="a3244-299">分類器を読み込む</span><span class="sxs-lookup"><span data-stu-id="a3244-299">Load a classifier</span></span>
> * <span data-ttu-id="a3244-300">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="a3244-300">Train the model</span></span>
> * <span data-ttu-id="a3244-301">別のデータ セットを使用してモデルを評価する</span><span class="sxs-lookup"><span data-stu-id="a3244-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="a3244-302">モデルを使用してテスト データの結果を予測する</span><span class="sxs-lookup"><span data-stu-id="a3244-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="a3244-303">さらに詳しく学習するには、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="a3244-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a3244-304">タクシー代予測</span><span class="sxs-lookup"><span data-stu-id="a3244-304">Taxi Fare Predictor</span></span>](taxi-fare.md)

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
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="62aff-103">チュートリアル: ML.NET を使用してニューヨークのタクシー運賃を予測する (回帰)</span><span class="sxs-lookup"><span data-stu-id="62aff-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="62aff-104">このトピックでは現在プレビュー段階である ML.NET を参照しており、資料が変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="62aff-105">詳しくは、[ML.NET の概要](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62aff-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="62aff-106">このチュートリアルでは、ML.NET を使用して、ニューヨーク市のタクシー運賃を予測する[回帰モデル](../resources/glossary.md#regression)を構築する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="62aff-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="62aff-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="62aff-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="62aff-108">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="62aff-108">Understand the problem</span></span>
> * <span data-ttu-id="62aff-109">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="62aff-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="62aff-110">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="62aff-110">Prepare and understand your data</span></span>
> * <span data-ttu-id="62aff-111">学習パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="62aff-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="62aff-112">データを読み込んで変換する</span><span class="sxs-lookup"><span data-stu-id="62aff-112">Load and transform your data</span></span>
> * <span data-ttu-id="62aff-113">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="62aff-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="62aff-114">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="62aff-114">Train the model</span></span>
> * <span data-ttu-id="62aff-115">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="62aff-115">Evaluate the model</span></span>
> * <span data-ttu-id="62aff-116">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="62aff-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62aff-117">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="62aff-117">Prerequisites</span></span>

* <span data-ttu-id="62aff-118">[Visual Studio 2017 15.6 以降](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" とともにインストールされていること。</span><span class="sxs-lookup"><span data-stu-id="62aff-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="62aff-119">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="62aff-119">Understand the problem</span></span>

<span data-ttu-id="62aff-120">この問題の中心となるのは、**ニューヨーク市のタクシー旅行の運賃の予測**です。</span><span class="sxs-lookup"><span data-stu-id="62aff-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="62aff-121">一見すると、単に乗車距離に依存すると思われるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="62aff-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="62aff-122">しかし、ニューヨークのタクシー会社は追加の乗客数や現金でなくクレジット カードによる支払いなど、その他の要因によって請求額を変えます。</span><span class="sxs-lookup"><span data-stu-id="62aff-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="62aff-123">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="62aff-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="62aff-124">タクシー運賃を予測するには、最初に適切な機械学習タスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="62aff-125">ここでは、データ セット内のその他の要因に基づいて実際の値 (価格を表す倍精度値) を予測しようとしています。</span><span class="sxs-lookup"><span data-stu-id="62aff-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="62aff-126">そのため、[**回帰**](../resources/glossary.md#regression)タスクを選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

<span data-ttu-id="62aff-127">モデルのトレーニングのプロセスでは、最終的な運賃の予測の際に最も大きな影響を与えたデータ セット内の要因を特定します。</span><span class="sxs-lookup"><span data-stu-id="62aff-127">The process of training the model identifies which factors in the dataset are most influential when predicting the final fare price.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="62aff-128">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="62aff-128">Create a console application</span></span>

1. <span data-ttu-id="62aff-129">Visual Studio 2017 を開きます。</span><span class="sxs-lookup"><span data-stu-id="62aff-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="62aff-130">**[ファイル]** > **[新規作成]** > **[プロジェクト]** をメニュー バーから選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="62aff-131">**[新しいプロジェクト]** ダイアログで、**[Visual C#]** ノードを選択し、**[.NET Core]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="62aff-132">次に、**[コンソール アプリ (.NET Core)]** プロジェクト テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="62aff-133">**[名前]** テキスト ボックスに「TaxiFarePrediction」と入力し、**[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="62aff-134">プロジェクトに *Data* という名前のディレクトリを作成して、データ セット ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="62aff-134">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="62aff-135">**ソリューション エクスプローラー**で、使用するプロジェクトを右クリックし、**[追加]** > **[新しいフォルダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-135">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="62aff-136">「Data」と入力して Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="62aff-136">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="62aff-137">**Microsoft.ML NuGet パッケージ**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="62aff-137">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="62aff-138">ソリューション エクスプローラーで、使用するプロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-138">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="62aff-139">[パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、**[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-139">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="62aff-140">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、**[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-and-understand-your-data"></a><span data-ttu-id="62aff-141">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="62aff-141">Prepare and understand your data</span></span>

1. <span data-ttu-id="62aff-142">[taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) データ セットと [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) データ セットをダウンロードして、作成済みの *Data* フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="62aff-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="62aff-143">Taxi Trip データ セットは、機械学習モデルをトレーニングします。このデータ セットを使用すると、モデルの正確性を評価できます。</span><span class="sxs-lookup"><span data-stu-id="62aff-143">The Taxi Trip data set trains the machine learning model and can be used to evaluate how accurate your model is.</span></span> <span data-ttu-id="62aff-144">これらのデータ セットは、[NYC TLC Taxi Trip データ セット](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)から取得したものです。</span><span class="sxs-lookup"><span data-stu-id="62aff-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="62aff-145">ソリューション エクスプローラーで、各 \*.csv ファイルを右クリックし、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="62aff-146">**[詳細設定]** で、**[出力ディレクトリにコピー]** の値を **[常時]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="62aff-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="62aff-147">**taxi-fare-train.csv** データ セットをコード エディターで開き、最初の行の列ヘッダーを確認します。</span><span class="sxs-lookup"><span data-stu-id="62aff-147">Open the **taxi-fare-train.csv** data set in the code editor and look at column headers in the first row.</span></span> <span data-ttu-id="62aff-148">各列を確認してください。</span><span class="sxs-lookup"><span data-stu-id="62aff-148">Take a look at each of the columns.</span></span> <span data-ttu-id="62aff-149">データについて把握し、どの列が**特徴**および**ラベル**であるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="62aff-149">Understand the data and decide which columns are **features** and which is the **label**.</span></span>

<span data-ttu-id="62aff-150">**ラベル**は、予測しようとしている列の識別子です。</span><span class="sxs-lookup"><span data-stu-id="62aff-150">The **label** is the identifier of the column you are trying to predict.</span></span> <span data-ttu-id="62aff-151">識別された**特徴**は、ラベルを予測するために使用します。</span><span class="sxs-lookup"><span data-stu-id="62aff-151">The identified **features** are used to predict the label.</span></span>

* <span data-ttu-id="62aff-152">**vendor_id:** タクシー会社の ID は特徴です。</span><span class="sxs-lookup"><span data-stu-id="62aff-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="62aff-153">**rate_code:** タクシー旅行のレートの種類は特徴です。</span><span class="sxs-lookup"><span data-stu-id="62aff-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="62aff-154">**passenger_count:** 旅行の乗客数は特徴です。</span><span class="sxs-lookup"><span data-stu-id="62aff-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="62aff-155">**trip_time_in_secs:** 旅行の所要時間です。</span><span class="sxs-lookup"><span data-stu-id="62aff-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="62aff-156">旅行の所要時間は旅行が終わるまでわかりません。</span><span class="sxs-lookup"><span data-stu-id="62aff-156">You won't know how long the trip takes until after it is completed.</span></span> <span data-ttu-id="62aff-157">この列はモデルから除外します。</span><span class="sxs-lookup"><span data-stu-id="62aff-157">You exclude this column from the model.</span></span>
* <span data-ttu-id="62aff-158">**trip_distance:** 旅行距離は特徴です。</span><span class="sxs-lookup"><span data-stu-id="62aff-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="62aff-159">**payment_type:** 支払い方法 (現金またはクレジット カード) は特徴です。</span><span class="sxs-lookup"><span data-stu-id="62aff-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="62aff-160">**fare_amount:** 支払った合計タクシー運賃はラベルです。</span><span class="sxs-lookup"><span data-stu-id="62aff-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="62aff-161">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="62aff-161">Create classes and define paths</span></span>

<span data-ttu-id="62aff-162">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-162">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="62aff-163">最近ダウンロードしたファイルのパスを保持し、モデルを保存する 3 つのグローバル変数を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-163">You need to create three global variables to hold the paths to the recently downloaded files and to save the model:</span></span>

* <span data-ttu-id="62aff-164">`_datapath` には、モデルのトレーニングに使用するデータ セットのパスがあります。</span><span class="sxs-lookup"><span data-stu-id="62aff-164">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="62aff-165">`_testdatapath` には、モデルの評価に使用するデータ セットのパスがあります。</span><span class="sxs-lookup"><span data-stu-id="62aff-165">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="62aff-166">`_modelpath` には、トレーニング済みのモデルを格納するパスがあります。</span><span class="sxs-lookup"><span data-stu-id="62aff-166">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="62aff-167">`Main` のすぐ上にある行に次のコードを追加して、最近ダウンロードしたファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="62aff-167">Add the following code to the line right above `Main` to specify the recently downloaded files:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="62aff-168">次に、入力データと予測のためのクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="62aff-168">Next, create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="62aff-169">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-169">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="62aff-170">**[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TaxiTrip.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="62aff-170">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="62aff-171">次に、**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-171">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="62aff-172">新しいファイルに次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-172">Add the following `using` statements to the new file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="62aff-173">既存のクラス定義を削除し、2 つのクラス `TaxiTrip` と `TaxiTripFarePrediction` を含む次のコードを *TaxiTrip.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-173">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="62aff-174">`TaxiTrip` は入力データ セット クラスであり、各データ セット列の定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="62aff-174">`TaxiTrip` is the input data set class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="62aff-175">`TaxiTripFarePrediction` クラスは、モデルのトレーニング後の予測に使用します。</span><span class="sxs-lookup"><span data-stu-id="62aff-175">The `TaxiTripFarePrediction` class is used for prediction after the model has been trained.</span></span> <span data-ttu-id="62aff-176">このクラスには 1 つの浮動小数点 (`FareAmount`) および [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 属性を適用した `Score` が格納されています。</span><span class="sxs-lookup"><span data-stu-id="62aff-176">It has a single float (`FareAmount`) and a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span>

<span data-ttu-id="62aff-177">**Program.cs** ファイルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="62aff-177">Now go back to the **Program.cs** file.</span></span> <span data-ttu-id="62aff-178">`Main` で、`Console.WriteLine("Hello World!")` を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="62aff-178">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="62aff-179">`Train` メソッドは、モデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="62aff-179">The `Train` method trains your model.</span></span> <span data-ttu-id="62aff-180">次のコードを使用して、`Main` の直下にその関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="62aff-180">Create that function just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="62aff-181">学習パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="62aff-181">Create a learning pipeline</span></span>

<span data-ttu-id="62aff-182">学習パイプラインは、モデルのトレーニングに必要なすべてのデータとアルゴリズムを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="62aff-182">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="62aff-183">`Train()` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-183">Add the following code into the `Train()` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a><span data-ttu-id="62aff-184">データを読み込んで変換する</span><span class="sxs-lookup"><span data-stu-id="62aff-184">Load and transform your data</span></span>

<span data-ttu-id="62aff-185">次に、パイプラインにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="62aff-185">Next, load your data into the pipeline.</span></span> <span data-ttu-id="62aff-186">最初に作成した `_datapath` をポイントして、.csv ファイルの区切り記号 (,) を指定します。</span><span class="sxs-lookup"><span data-stu-id="62aff-186">Point to the `_datapath` created initially and specify the delimiter of the .csv file (,).</span></span> <span data-ttu-id="62aff-187">最後のステップの下にある `Train()` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-187">Add the following code into the `Train()` method underneath the last step:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

<span data-ttu-id="62aff-188">作成するコードでは、アンダースコアのない列を参照します。</span><span class="sxs-lookup"><span data-stu-id="62aff-188">You'll refer to the columns without the underscores in the code you're creating.</span></span> <span data-ttu-id="62aff-189">`ColumnCopier()` 関数を使用して、`FareAmount` 列を "Label" という名前の新しい列にコピーします。</span><span class="sxs-lookup"><span data-stu-id="62aff-189">Copy the `FareAmount` column into a new column called "Label" using the `ColumnCopier()` function.</span></span> <span data-ttu-id="62aff-190">この列は**ラベル**です。</span><span class="sxs-lookup"><span data-stu-id="62aff-190">This column is the **Label**.</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="62aff-191">**特徴エンジニアリング**を実行してデータを変換し、機械学習でデータを効果的に使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="62aff-191">Conduct some **feature engineering** to transform the data so that it can be used effectively for machine learning.</span></span> <span data-ttu-id="62aff-192">モデルをトレーニングするアルゴリズムには、**数値**の特徴が必要であるため、カテゴリ データ (`VendorId`、`RateCode`、および `PaymentType`) を数字に変換します。</span><span class="sxs-lookup"><span data-stu-id="62aff-192">The algorithm that trains the model requires **numeric** features, you transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) into numbers.</span></span> <span data-ttu-id="62aff-193">`CategoricalOneHotVectorizer()` 関数は、これらの各列の値に数値キーを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="62aff-193">The `CategoricalOneHotVectorizer()` function assigns a numeric key to the values in each of these columns.</span></span> <span data-ttu-id="62aff-194">このコードを追加することで、データを変換します。</span><span class="sxs-lookup"><span data-stu-id="62aff-194">Transform your data by adding this code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="62aff-195">データ準備の最後の手順は、`ColumnConcatenator()` 関数を使用して、すべての**特徴**を 1 つのベクトルに結合することです。</span><span class="sxs-lookup"><span data-stu-id="62aff-195">The last step in data preparation combines all of your **features** into one vector using the `ColumnConcatenator()` function.</span></span> <span data-ttu-id="62aff-196">この必須の手順によって、アルゴリズムが特徴を簡単に処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="62aff-196">This necessary step helps the algorithm easily process your features.</span></span> <span data-ttu-id="62aff-197">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-197">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="62aff-198">`trip_time_in_secs` 列が含まれていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="62aff-198">Notice that the `trip_time_in_secs` column isn't included.</span></span> <span data-ttu-id="62aff-199">既に確認したとおり、この列は有効な予測特徴ではありません。</span><span class="sxs-lookup"><span data-stu-id="62aff-199">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="62aff-200">これらの手順を成功させるには、前述の指定した順序でパイプラインに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-200">These steps must be added to Pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="62aff-201">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="62aff-201">Choose a learning algorithm</span></span>

<span data-ttu-id="62aff-202">データをパイプラインに追加して正しい入力形式に変換したら、学習アルゴリズム (**ラーナー**) を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-202">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="62aff-203">学習アルゴリズムは、モデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="62aff-203">The learning algorithm trains the model.</span></span> <span data-ttu-id="62aff-204">この問題に対しては**回帰タスク**を選択済みであるため、**勾配ブースティング**を利用するパイプラインに `FastTreeRegressor()` というラーナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-204">You chose a **regression task** for this problem, so you add a learner called `FastTreeRegressor()` to the pipeline that utilizes **gradient boosting**.</span></span>

<span data-ttu-id="62aff-205">勾配ブースティングは、回帰問題に対応する機械学習の手法です。</span><span class="sxs-lookup"><span data-stu-id="62aff-205">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="62aff-206">この手法では、それぞれの回帰ツリーを段階的に構築します。</span><span class="sxs-lookup"><span data-stu-id="62aff-206">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="62aff-207">また、定義済みの損失関数を使用して、各ステップの誤差を測定し、次の段階で修正します。</span><span class="sxs-lookup"><span data-stu-id="62aff-207">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="62aff-208">結果は予測モデルですが、実際は弱い予測モデルの集合です。</span><span class="sxs-lookup"><span data-stu-id="62aff-208">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="62aff-209">勾配ブースティングについて詳しくは、「[Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression)」(ブーストされたデシジョン ツリー回帰) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62aff-209">For more information about gradient boosting, see [Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="62aff-210">前の手順で追加したデータ処理コードの後にある `Train()` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-210">Add the following code into the `Train()` method following the data processing code added in the last step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="62aff-211">前述のすべての手順は個々のステートメントとしてパイプラインに追加しましたが、C# には使いやすいコレクションの初期化構文があるため、パイプラインの作成と初期化が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="62aff-211">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="62aff-212">次のコードを使用して、これまでに追加したコードを `Train()` メソッドに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="62aff-212">Replace the code you added so far to the `Train()` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="62aff-213">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="62aff-213">Train the model</span></span>

<span data-ttu-id="62aff-214">最後の手順は、モデルのトレーニングです。</span><span class="sxs-lookup"><span data-stu-id="62aff-214">The final step is to train the model.</span></span> <span data-ttu-id="62aff-215">ここまで、パイプライン内の項目は何も実行されていません。</span><span class="sxs-lookup"><span data-stu-id="62aff-215">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="62aff-216">`pipeline.Train<T_Input, T_Output>()` 関数は、定義済みの `TaxiTrip`クラス型を受け入れて、`TaxiTripFarePrediction` 型を出力します。</span><span class="sxs-lookup"><span data-stu-id="62aff-216">The `pipeline.Train<T_Input, T_Output>()` function takes in the pre-defined `TaxiTrip` class type and outputs a `TaxiTripFarePrediction` type.</span></span> <span data-ttu-id="62aff-217">この最後のコード部分を `Train()` 関数に追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-217">Add this final piece of code into the `Train()` function:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="62aff-218">以上です。</span><span class="sxs-lookup"><span data-stu-id="62aff-218">And that's it!</span></span> <span data-ttu-id="62aff-219">これで機械学習モデルのトレーニングが終了し、ニューヨーク市のタクシー運賃を予測できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="62aff-219">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="62aff-220">それでは、モデルの正確性と使い方を確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="62aff-220">Now take a look to understand how accurate your model is and learn how to consume it.</span></span>

## <a name="save-the-model"></a><span data-ttu-id="62aff-221">モデルを保存する</span><span class="sxs-lookup"><span data-stu-id="62aff-221">Save the model</span></span>

<span data-ttu-id="62aff-222">次の手順に進む前に、`Train()` 関数の末尾に次のコードを追加して、モデルを .zip ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="62aff-222">Before you go onto the next step, save your model to a .zip file by adding the following code at the end of your `Train()` function:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="62aff-223">`model.WriteAsync()` の呼び出しに `await` ステートメントを追加した場合は、`Train()` メソッドを `Task` を返す非同期メソッドに変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-223">Adding the `await` statement to the `model.WriteAsync()` call means that the `Train()` method must be changed to an async method that returns a `Task`.</span></span> <span data-ttu-id="62aff-224">次のコードに示すように、`Train` のシグネチャを変更します。</span><span class="sxs-lookup"><span data-stu-id="62aff-224">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="62aff-225">`Train` メソッドの戻り値の型を変更した場合は、次のコードに示すように、`Main` メソッドで `Train` を呼び出すコードに `await` を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-225">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="62aff-226">`Main` メソッドに `await` を追加した場合は、`Main` メソッドに `async` 修飾子が必要です。このメソッドは `Task` を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-226">Adding an `await` in your `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="62aff-227">また、次の using ステートメントをファイルの先頭に追加する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="62aff-227">You also need to add the following using statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="62aff-228">`async Main` メソッドは C# 7.1 の新機能であり、プロジェクトの既定の言語バージョンは C# 7.0 であるため、言語バージョンを C# 7.1 以降に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62aff-228">Because the `async Main` method is a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="62aff-229">そのためには、**ソリューション エクスプローラー**でプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-229">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="62aff-230">**[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-230">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="62aff-231">ドロップダウンで **[C# 7.1]** (またはそれ以降のバージョン) を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-231">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="62aff-232">**[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-232">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="62aff-233">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="62aff-233">Evaluate the model</span></span>

<span data-ttu-id="62aff-234">評価は、モデルが適切に機能するかどうかを確認するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="62aff-234">Evaluation is the process of checking how well the model works.</span></span> <span data-ttu-id="62aff-235">トレーニング時には使用しなかったデータを適切に予測できるかどうかが重要になります。</span><span class="sxs-lookup"><span data-stu-id="62aff-235">It's important that your model makes good predictions on data that it didn't use when it was trained.</span></span> <span data-ttu-id="62aff-236">そのための方法の 1 つとしては、このチュートリアルで行ったように、データをトレーニング用のデータ セットとテスト用のデータ セットに分けます。</span><span class="sxs-lookup"><span data-stu-id="62aff-236">One way to do this is by splitting the data into train and test datasets, as you did in this tutorial.</span></span> <span data-ttu-id="62aff-237">トレーニング用データでのモデルのトレーニングは完了しているので、テスト用データでモデルが適切に機能するかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="62aff-237">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="62aff-238">`Main` 関数に戻り、`Train()` メソッドの呼び出しの下に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-238">Go back to your `Main` function and add the following code beneath the call to the `Train()`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="62aff-239">`Evaluate()` 関数はモデルを評価します。</span><span class="sxs-lookup"><span data-stu-id="62aff-239">The `Evaluate()` function evaluates your model.</span></span> <span data-ttu-id="62aff-240">その関数を `Train()` の下に作成します。</span><span class="sxs-lookup"><span data-stu-id="62aff-240">Create that function below `Train()`.</span></span> <span data-ttu-id="62aff-241">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-241">Add the following code:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="62aff-242">`TextLoader()` 関数を使用して、テスト用データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="62aff-242">Load the test data using the `TextLoader()` function.</span></span> <span data-ttu-id="62aff-243">`Evaluate()` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-243">Add the following code into the `Evaluate()` method:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="62aff-244">モデルを評価する次のコードを追加して、メトリックを生成します。</span><span class="sxs-lookup"><span data-stu-id="62aff-244">Add the following code to evaluate the model and produce the metrics for it:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="62aff-245">RMS は、回帰問題を評価するための 1 つのメトリックです。</span><span class="sxs-lookup"><span data-stu-id="62aff-245">RMS is one metric for evaluating regression problems.</span></span> <span data-ttu-id="62aff-246">RMS が低いほど優れたモデルになります。</span><span class="sxs-lookup"><span data-stu-id="62aff-246">The lower it is, the better your model.</span></span> <span data-ttu-id="62aff-247">`Evaluate()` 関数に次のコードを追加して、モデルの RMS を出力します。</span><span class="sxs-lookup"><span data-stu-id="62aff-247">Add the following code into the `Evaluate()` function to print the RMS for your model.</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="62aff-248">RSquared は、回帰問題を評価するためのもう 1 つのメトリックです。</span><span class="sxs-lookup"><span data-stu-id="62aff-248">RSquared is another metric for evaluating regression problems.</span></span> <span data-ttu-id="62aff-249">RSquared の値は 0 ～ 1 です。</span><span class="sxs-lookup"><span data-stu-id="62aff-249">RSquared will be a value between 0 and 1.</span></span> <span data-ttu-id="62aff-250">1 に近づくほど優れたモデルになります。</span><span class="sxs-lookup"><span data-stu-id="62aff-250">The closer you are to 1, the better your model.</span></span> <span data-ttu-id="62aff-251">`Evaluate()` 関数に次のコードを追加して、モデルの RSquared 値を出力します。</span><span class="sxs-lookup"><span data-stu-id="62aff-251">Add the following code into the `Evaluate()` function to print the RSquared value for your model.</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="62aff-252">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="62aff-252">Use the model for predictions</span></span>

<span data-ttu-id="62aff-253">次に、モデルが正しく機能しているかどうかを確認するためのテスト シナリオを格納するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="62aff-253">Next, create a class to house test scenarios that you can use to make sure your model is working correctly:</span></span>

1. <span data-ttu-id="62aff-254">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、**[追加]** > **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-254">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="62aff-255">**[新しい項目の追加]** ダイアログ ボックスで、**[クラス]** を選択し、**[名前]** フィールドを *TestTrips.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="62aff-255">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="62aff-256">次に、**[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="62aff-256">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="62aff-257">次の例に示すように、静的になるようにクラスを変更します。</span><span class="sxs-lookup"><span data-stu-id="62aff-257">Modify the class to be static like in the following example:</span></span>

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="62aff-258">このチュートリアルでは、このクラス内の 1 つのテスト用の旅行を使用します。</span><span class="sxs-lookup"><span data-stu-id="62aff-258">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="62aff-259">このサンプルを試行するために、後で他のシナリオを追加できます。</span><span class="sxs-lookup"><span data-stu-id="62aff-259">Later you can add other scenarios to experiment with this sample.</span></span> <span data-ttu-id="62aff-260">`TestTrips` クラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-260">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="62aff-261">この旅行にかかった実際の運賃は 29.5 ですが、プレースホルダーとして 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="62aff-261">This trip's actual fare is 29.5, but use 0 as a placeholder.</span></span> <span data-ttu-id="62aff-262">機械学習アルゴリズムが運賃を予測します。</span><span class="sxs-lookup"><span data-stu-id="62aff-262">The machine learning algorithm will predict the fare.</span></span>

<span data-ttu-id="62aff-263">`Main` 関数に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="62aff-263">Add the following code in your `Main` function.</span></span> <span data-ttu-id="62aff-264">このコードで `TestTrip` データを使用してモデルをテストします。</span><span class="sxs-lookup"><span data-stu-id="62aff-264">It tests out your model using the `TestTrip` data:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="62aff-265">プログラムを実行し、テスト ケースに対して予測されたタクシー運賃を確認します。</span><span class="sxs-lookup"><span data-stu-id="62aff-265">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="62aff-266">おめでとうございます! </span><span class="sxs-lookup"><span data-stu-id="62aff-266">Congratulations!</span></span> <span data-ttu-id="62aff-267">これで、タクシー運賃を予測する機械学習モデルが構築されて、その正確性の評価とテストが完了しました。</span><span class="sxs-lookup"><span data-stu-id="62aff-267">You've now successfully built a machine learning model for predicting taxi fares, evaluated its accuracy, and tested it.</span></span> <span data-ttu-id="62aff-268">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="62aff-268">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="62aff-269">次の手順</span><span class="sxs-lookup"><span data-stu-id="62aff-269">Next steps</span></span>

<span data-ttu-id="62aff-270">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="62aff-270">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="62aff-271">問題を把握する</span><span class="sxs-lookup"><span data-stu-id="62aff-271">Understand the problem</span></span>
> * <span data-ttu-id="62aff-272">適切な機械学習タスクを選択する</span><span class="sxs-lookup"><span data-stu-id="62aff-272">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="62aff-273">データを準備して理解する</span><span class="sxs-lookup"><span data-stu-id="62aff-273">Prepare and understand your data</span></span>
> * <span data-ttu-id="62aff-274">学習パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="62aff-274">Create a learning pipeline</span></span>
> * <span data-ttu-id="62aff-275">データを読み込んで変換する</span><span class="sxs-lookup"><span data-stu-id="62aff-275">Load and transform your data</span></span>
> * <span data-ttu-id="62aff-276">学習アルゴリズムを選択する</span><span class="sxs-lookup"><span data-stu-id="62aff-276">Choose a learning algorithm</span></span>
> * <span data-ttu-id="62aff-277">モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="62aff-277">Train the model</span></span>
> * <span data-ttu-id="62aff-278">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="62aff-278">Evaluate the model</span></span>
> * <span data-ttu-id="62aff-279">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="62aff-279">Use the model for predictions</span></span>

<span data-ttu-id="62aff-280">学習を続けてその他のサンプルを確認するには、GitHub リポジトリをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="62aff-280">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="62aff-281">dotnet/machinelearning GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="62aff-281">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)

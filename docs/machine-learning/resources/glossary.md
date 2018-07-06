---
title: 機械学習の用語集
description: 機械学習の用語集。
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: b7690eb6931f4a491b1a03812fe3f2d8a64cfcd4
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207730"
---
# <a name="machine-learning-glossary"></a><span data-ttu-id="f17a0-103">機械学習の用語集</span><span class="sxs-lookup"><span data-stu-id="f17a0-103">Machine learning glossary</span></span>

<span data-ttu-id="f17a0-104">カスタム モデルをビルドする際に役立つ機械学習の重要な用語を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-104">The following list is a compilation of important machine learning terms that are useful as you build your custom models.</span></span>

## <a name="accuracy"></a><span data-ttu-id="f17a0-105">正確度</span><span class="sxs-lookup"><span data-stu-id="f17a0-105">Accuracy</span></span>

<span data-ttu-id="f17a0-106">[分類](#classification)における正確度は、正しく分類された項目の数をテスト セット内の項目の総数で割ったものです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-106">In [classification](#classification), accuracy is the number of correctly classified items divided by the total number of items in the test set.</span></span> <span data-ttu-id="f17a0-107">0 (正確度が最も低い) ～ 1 (正確度が最も高い) の値になります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-107">Ranges from 0 (least accurate) to 1 (most accurate).</span></span> <span data-ttu-id="f17a0-108">正確度は、モデルのパフォーマンスの評価メトリックの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-108">Accuracy is one of evaluation metrics of the performance of your model.</span></span> <span data-ttu-id="f17a0-109">[精度](#precision)、[再現率](#recall)、および [F 値](#f-score)と併せて考慮してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-109">Consider it in conjunction with [precision](#precision), [recall](#recall), and [F-score](#f-score).</span></span>

<span data-ttu-id="f17a0-110">関連する ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-110">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.</span></span>

## <a name="area-under-the-curve-auc"></a><span data-ttu-id="f17a0-111">曲線下面積 (AUC)</span><span class="sxs-lookup"><span data-stu-id="f17a0-111">Area under the curve (AUC)</span></span>

<span data-ttu-id="f17a0-112">[二項分類](#binary-classification)における評価メトリックであり、偽陽性率 (x 軸上) に対する真陽性率 (y 軸上) を描画する曲線下面積の値です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-112">In [binary classification](#binary-classification), an evaluation metric that is the value of the area under the curve that plots the true positives rate (on the y-axis) against the false positives rate (on the x-axis).</span></span> <span data-ttu-id="f17a0-113">0.5 (最低) ～ 1 (最高) の値になります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-113">Ranges from 0.5 (worst) to 1 (best).</span></span> <span data-ttu-id="f17a0-114">ROC 曲線 (受信者操作特性曲線) 下面積とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-114">Also known as the area under the ROC curve, i.e., receiver operating characteristic curve.</span></span> <span data-ttu-id="f17a0-115">詳しくは、Wikipedia の[受信者操作特性](https://en.wikipedia.org/wiki/Receiver_operating_characteristic)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-115">For more information, see the [Receiver operating characteristic](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) article on Wikipedia.</span></span>

<span data-ttu-id="f17a0-116">関連する ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-116">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="f17a0-117">二項分類</span><span class="sxs-lookup"><span data-stu-id="f17a0-117">Binary classification</span></span>

<span data-ttu-id="f17a0-118">[ラベル](#label)が 2 つのクラスのうちの 1 つである[分類](#classification)です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-118">A [classification](#classification) case where the [label](#label) is only one out of two classes.</span></span> <span data-ttu-id="f17a0-119">詳細については、トピック「[機械学習のタスク](tasks.md)」のセクションの「[二項分類](tasks.md#binary-classification)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-119">For more information, see the [Binary classification](tasks.md#binary-classification) section of the [Machine learning tasks](tasks.md) topic.</span></span>

## <a name="classification"></a><span data-ttu-id="f17a0-120">分類</span><span class="sxs-lookup"><span data-stu-id="f17a0-120">Classification</span></span>

<span data-ttu-id="f17a0-121">データを使用してカテゴリを予測する際、[教師あり機械学習](#supervised-machine-learning)タスクが分類と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-121">When the data is used to predict a category, [supervised machine learning](#supervised-machine-learning) task is called classification.</span></span> <span data-ttu-id="f17a0-122">[二項分類](#binary-classification)とは、2 つのカテゴリだけを予測する (たとえば、画像を猫または犬の写真として分類する) ことです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-122">[Binary classification](#binary-classification) refers to predicting only two categories (for example, classifying an image as a picture of either a 'cat' or a 'dog').</span></span> <span data-ttu-id="f17a0-123">[多クラス分類](#multiclass-classification)とは、複数のカテゴリを予測する (たとえば、画像を特定の犬種の写真として分類する) ことです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-123">[Multiclass classification](#multiclass-classification) refers to predicting multiple categories (for example, when classifying an image as a picture of a specific breed of dog).</span></span>

## <a name="coefficient-of-determination"></a><span data-ttu-id="f17a0-124">決定係数</span><span class="sxs-lookup"><span data-stu-id="f17a0-124">Coefficient of determination</span></span>

<span data-ttu-id="f17a0-125">[回帰](#regression)における評価メトリックであり、データがモデルにどの程度適合するかを示します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-125">In [regression](#regression), an evaluation metric that indicates how well data fits a model.</span></span> <span data-ttu-id="f17a0-126">0 ～ 1 の値になります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-126">Ranges from 0 to 1.</span></span> <span data-ttu-id="f17a0-127">値 0 は、データがランダムであるか、モデルに適合できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-127">A value of 0 means that the data is random or otherwise cannot be fit to the model.</span></span> <span data-ttu-id="f17a0-128">値 1 は、モデルがデータと完全に一致していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-128">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="f17a0-129">多くの場合、これは r<sup>2</sup>、R<sup>2</sup>、または r の 2 乗と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-129">This is often referred to as r<sup>2</sup>, R<sup>2</sup>, or r-squared.</span></span>

<span data-ttu-id="f17a0-130">関連する ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-130">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.</span></span>

## <a name="feature"></a><span data-ttu-id="f17a0-131">機能</span><span class="sxs-lookup"><span data-stu-id="f17a0-131">Feature</span></span>

<span data-ttu-id="f17a0-132">測定対象となる事象の測定可能なプロパティです。通常は数 (倍精度) 値になります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-132">A measurable property of the phenomenon being measured, typically a numeric (double) value.</span></span> <span data-ttu-id="f17a0-133">複数の特徴は**特徴ベクトル**と呼ばれ、通常は `double[]` として格納されます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-133">Multiple features are referred to as a **Feature vector** and typically stored as `double[]`.</span></span> <span data-ttu-id="f17a0-134">特徴では、測定対象となる事象の重要な特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-134">Features define the important characteristics of the phenomenon being measured.</span></span> <span data-ttu-id="f17a0-135">詳しくは、Wikipedia の[特徴](https://en.wikipedia.org/wiki/Feature_(machine_learning))の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-135">For more information, see the [Feature](https://en.wikipedia.org/wiki/Feature_(machine_learning)) article on Wikipedia.</span></span>

## <a name="feature-engineering"></a><span data-ttu-id="f17a0-136">特徴エンジニアリング</span><span class="sxs-lookup"><span data-stu-id="f17a0-136">Feature engineering</span></span>

<span data-ttu-id="f17a0-137">特徴エンジニアリングは、一連の[特徴](#feature)の定義、および使用可能な事象データから特徴ベクトルを生成する (特徴抽出) ソフトウェアの開発を含むプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-137">Feature engineering is the process that involves defining a set of [features](#feature) and developing software that produces feature vectors from available phenomenon data, i.e., feature extraction.</span></span> <span data-ttu-id="f17a0-138">詳しくは、Wikipedia の[特徴エンジニアリング](https://en.wikipedia.org/wiki/Feature_engineering)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-138">For more information, see the [Feature engineering](https://en.wikipedia.org/wiki/Feature_engineering) article on Wikipedia.</span></span>

## <a name="f-score"></a><span data-ttu-id="f17a0-139">F 値</span><span class="sxs-lookup"><span data-stu-id="f17a0-139">F-score</span></span>

<span data-ttu-id="f17a0-140">[分類](#classification)における評価メトリックであり、[精度](#precision)と[再現率](#recall)の調和平均を取ります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-140">In [classification](#classification), an evaluation metric that balances [precision](#precision) and [recall](#recall).</span></span>

<span data-ttu-id="f17a0-141">関連する ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-141">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.</span></span>

## <a name="hyperparameter"></a><span data-ttu-id="f17a0-142">ハイパーパラメーター</span><span class="sxs-lookup"><span data-stu-id="f17a0-142">Hyperparameter</span></span>

<span data-ttu-id="f17a0-143">機械学習アルゴリズムのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-143">A parameter of a machine learning algorithm.</span></span> <span data-ttu-id="f17a0-144">例として、デシジョン フォレストにおける学習するツリー数や勾配降下アルゴリズムにおけるステップ サイズなどがあります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-144">Examples include the number of trees to learn in a decision forest or the step size in a gradient descent algorithm.</span></span> <span data-ttu-id="f17a0-145">*ハイパーパラメーター*の値は、モデルのトレーニング前に設定され、予測関数のパラメーターを検出するプロセスを管理します。例として、デシジョン ツリーにおける比較ポイントや線形回帰モデルにおける重みなどがあります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-145">Values of *Hyperparameters* are set before training the model and govern the process of finding the parameters of the prediction function, for example, the comparison points in a decision tree or the weights in a linear regression model.</span></span> <span data-ttu-id="f17a0-146">詳しくは、Wikipedia の[ハイパーパラメーター](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning))の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-146">For more information, see the [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) article on Wikipedia.</span></span>

## <a name="label"></a><span data-ttu-id="f17a0-147">group1</span><span class="sxs-lookup"><span data-stu-id="f17a0-147">Label</span></span>

<span data-ttu-id="f17a0-148">機械学習モデルで予測される要素です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-148">The element to be predicted with the machine learning model.</span></span> <span data-ttu-id="f17a0-149">たとえば、犬種や将来の株価などです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-149">For example, the breed of dog or a future stock price.</span></span>

## <a name="log-loss"></a><span data-ttu-id="f17a0-150">対数損失</span><span class="sxs-lookup"><span data-stu-id="f17a0-150">Log loss</span></span>

<span data-ttu-id="f17a0-151">[分類](#classification)における評価メトリックであり、分類子の正確度を示します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-151">In [classification](#classification), an evaluation metric that characterizes the accuracy of a classifier.</span></span> <span data-ttu-id="f17a0-152">対数損失が小さいほど、分類子の正確度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-152">The smaller log loss is, the more accurate a classifier is.</span></span>

<span data-ttu-id="f17a0-153">関連する ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-153">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.</span></span>

## <a name="mean-absolute-error-mae"></a><span data-ttu-id="f17a0-154">平均絶対誤差 (MAE)</span><span class="sxs-lookup"><span data-stu-id="f17a0-154">Mean absolute error (MAE)</span></span>

<span data-ttu-id="f17a0-155">[回帰](#regression)における評価メトリックであり、すべてのモデルの誤差の平均です。モデルの誤差とは、予測された[ラベル](#label)値と正確なラベル値の間の距離です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-155">In [regression](#regression), an evaluation metric that is the average of all the model errors, where model error is the distance between the predicted [label](#label) value and the correct label value.</span></span>

<span data-ttu-id="f17a0-156">関連する ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-156">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.</span></span>

## <a name="model"></a><span data-ttu-id="f17a0-157">モデル</span><span class="sxs-lookup"><span data-stu-id="f17a0-157">Model</span></span>

<span data-ttu-id="f17a0-158">従来的に予測関数のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-158">Traditionally, the parameters for the prediction function.</span></span> <span data-ttu-id="f17a0-159">たとえば、線形回帰モデルにおける重みやデシジョン ツリーにおける分割ポイントなどがあります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-159">For example, the weights in a linear regression model or the split points in a decision tree.</span></span> <span data-ttu-id="f17a0-160">ML.NET では、ドメイン オブジェクト (画像、テキストなど) の[ラベル](#label)の予測に必要なすべての情報がモデルに含まれます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-160">In ML.NET, a model contains all the information necessary to predict the [label](#label) of a domain object (for example, image or text).</span></span> <span data-ttu-id="f17a0-161">つまり、ML.NET モデルには、必要な特徴付けのステップと予測関数のパラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-161">This means that ML.NET models include the featurization steps necessary as well as the parameters for the prediction function.</span></span>

## <a name="multiclass-classification"></a><span data-ttu-id="f17a0-162">多クラス分類</span><span class="sxs-lookup"><span data-stu-id="f17a0-162">Multiclass classification</span></span>

<span data-ttu-id="f17a0-163">[ラベル](#label)が 3 つ以上のクラスのうちの 1 つである[分類](#classification)です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-163">A [classification](#classification) case where the [label](#label) is one out of three or more classes.</span></span> <span data-ttu-id="f17a0-164">詳細については、トピック「[機械学習のタスク](tasks.md)」のセクション「[多クラス分類](tasks.md#multiclass-classification)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-164">For more information, see the [Multiclass classification](tasks.md#multiclass-classification) section of the [Machine learning tasks](tasks.md) topic.</span></span>

## <a name="n-gram"></a><span data-ttu-id="f17a0-165">N グラム</span><span class="sxs-lookup"><span data-stu-id="f17a0-165">N-gram</span></span>

<span data-ttu-id="f17a0-166">テキスト データの特徴抽出スキームです。N 個の単語のシーケンスが[特徴](#feature)値になります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-166">A feature extraction scheme for text data: any sequence of N words turns into a [feature](#feature) value.</span></span>

## <a name="numerical-feature-vector"></a><span data-ttu-id="f17a0-167">数値特徴ベクトル</span><span class="sxs-lookup"><span data-stu-id="f17a0-167">Numerical feature vector</span></span>

<span data-ttu-id="f17a0-168">数値でのみ構成される[特徴](#feature)ベクトルです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-168">A [feature](#feature) vector consisting only of numerical values.</span></span> <span data-ttu-id="f17a0-169">これは `double[]` に似ています。</span><span class="sxs-lookup"><span data-stu-id="f17a0-169">This is similar to `double[]`.</span></span>

## <a name="pipeline"></a><span data-ttu-id="f17a0-170">パイプライン</span><span class="sxs-lookup"><span data-stu-id="f17a0-170">Pipeline</span></span>

<span data-ttu-id="f17a0-171">モデルをデータ セットに適合させるために必要なすべての操作です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-171">All of the operations needed to fit a model to a data set.</span></span> <span data-ttu-id="f17a0-172">パイプラインは、データのインポート、変換、特徴付け、および学習の各ステップで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-172">A pipeline consists of data import, transformation, featurization, and learning steps.</span></span> <span data-ttu-id="f17a0-173">トレーニングが完了したパイプラインがモデルになります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-173">Once a pipeline is trained, it turns into a model.</span></span>

## <a name="precision"></a><span data-ttu-id="f17a0-174">有効桁数</span><span class="sxs-lookup"><span data-stu-id="f17a0-174">Precision</span></span>

<span data-ttu-id="f17a0-175">[分類](#classification)におけるクラスの精度は、そのクラスに属していると正確に予測された項目の数を、クラスに属していると予測された項目の総数で割ったものです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-175">In [classification](#classification), the precision for a class is the number of items correctly predicted as belonging to that class divided by the total number of items predicted as belonging to the class.</span></span>

<span data-ttu-id="f17a0-176">関連する ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>、<xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-176">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.</span></span>

## <a name="recall"></a><span data-ttu-id="f17a0-177">再現率</span><span class="sxs-lookup"><span data-stu-id="f17a0-177">Recall</span></span>

<span data-ttu-id="f17a0-178">[分類](#classification)におけるクラスの再現率は、そのクラスに属していると正確に予測された項目の数を、実際にクラスに属している項目の総数で割ったものです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-178">In [classification](#classification), the recall for a class is the number of items correctly predicted as belonging to that class divided by the total number of items that actually belong to the class.</span></span>

<span data-ttu-id="f17a0-179">関連する ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>、<xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-179">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.</span></span>

## <a name="regression"></a><span data-ttu-id="f17a0-180">回帰</span><span class="sxs-lookup"><span data-stu-id="f17a0-180">Regression</span></span>

<span data-ttu-id="f17a0-181">出力が実際の値 (たとえば、倍精度) である[教師あり機械学習](#supervised-machine-learning)タスクです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-181">A [supervised machine learning](#supervised-machine-learning) task where the output is a real value, for example, double.</span></span> <span data-ttu-id="f17a0-182">例として、株価の予測などがあります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-182">Examples include predicting stock prices.</span></span> <span data-ttu-id="f17a0-183">詳細については、トピック「[機械学習のタスク](tasks.md)」のセクション「[回帰](tasks.md#regression)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-183">For more information, see the [Regression](tasks.md#regression) section of the [Machine learning tasks](tasks.md) topic.</span></span>

## <a name="relative-absolute-error"></a><span data-ttu-id="f17a0-184">相対絶対誤差</span><span class="sxs-lookup"><span data-stu-id="f17a0-184">Relative absolute error</span></span>

<span data-ttu-id="f17a0-185">[回帰](#regression)における評価メトリックであり、すべての絶対誤差の合計を、正確な[ラベル](#label)値とすべての正確なラベル値の平均との間の距離の合計で割ったものです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-185">In [regression](#regression), an evaluation metric that is the sum of all absolute errors divided by the sum of distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="relative-squared-error"></a><span data-ttu-id="f17a0-186">相対平方誤差</span><span class="sxs-lookup"><span data-stu-id="f17a0-186">Relative squared error</span></span>

<span data-ttu-id="f17a0-187">[回帰](#regression)における評価メトリックであり、すべての平方絶対誤差の合計を、正確な[ラベル](#label)値とすべての正確なラベル値の平均との間の平方距離の合計で割ったものです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-187">In [regression](#regression), an evaluation metric that is the sum of all squared absolute errors divided by the sum of squared distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="root-of-mean-squared-error-rmse"></a><span data-ttu-id="f17a0-188">平均平方誤差の平方根 (RMSE)</span><span class="sxs-lookup"><span data-stu-id="f17a0-188">Root of mean squared error (RMSE)</span></span>

<span data-ttu-id="f17a0-189">[回帰](#regression)における評価メトリックであり、誤差を 2 乗した値の平均値の平方根です。</span><span class="sxs-lookup"><span data-stu-id="f17a0-189">In [regression](#regression), an evaluation metric that is the square root of the average of the squares of the errors.</span></span>

<span data-ttu-id="f17a0-190">関連する ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f17a0-190">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.</span></span>

## <a name="supervised-machine-learning"></a><span data-ttu-id="f17a0-191">教師あり機械学習</span><span class="sxs-lookup"><span data-stu-id="f17a0-191">Supervised machine learning</span></span>

<span data-ttu-id="f17a0-192">機械学習の 1 つの手法であり、目的となるモデルが未知のデータのラベルを予測します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-192">A subclass of machine learning in which a desired model predicts the label for yet-unseen data.</span></span> <span data-ttu-id="f17a0-193">例として、分類、回帰、構造化予測などがあります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-193">Examples include classification, regression, and structured prediction.</span></span> <span data-ttu-id="f17a0-194">詳しくは、Wikipedia の[教師あり学習](https://en.wikipedia.org/wiki/Supervised_learning)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-194">For more information, see the  [Supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) article on Wikipedia.</span></span>

## <a name="training"></a><span data-ttu-id="f17a0-195">トレーニング</span><span class="sxs-lookup"><span data-stu-id="f17a0-195">Training</span></span>

<span data-ttu-id="f17a0-196">特定のトレーニング データ セットの[モデル](#model)を識別するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-196">The process of identifying a [model](#model) for a given training data set.</span></span> <span data-ttu-id="f17a0-197">線形モデルの場合、重みの検出を意味します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-197">For a linear model, this means finding the weights.</span></span> <span data-ttu-id="f17a0-198">ツリーの場合、分割ポイントの識別が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f17a0-198">For a tree, it involves the identifying the split points.</span></span>

## <a name="transform"></a><span data-ttu-id="f17a0-199">変換</span><span class="sxs-lookup"><span data-stu-id="f17a0-199">Transform</span></span>

<span data-ttu-id="f17a0-200">データを変換する[パイプライン](#pipeline) コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-200">A [pipeline](#pipeline) component that transforms data.</span></span> <span data-ttu-id="f17a0-201">たとえば、数字のテキストからベクトルへの変換などです。</span><span class="sxs-lookup"><span data-stu-id="f17a0-201">For example, from text to vector of numbers.</span></span>

## <a name="unsupervised-machine-learning"></a><span data-ttu-id="f17a0-202">教師なし機械学習</span><span class="sxs-lookup"><span data-stu-id="f17a0-202">Unsupervised machine learning</span></span>

<span data-ttu-id="f17a0-203">機械学習の 1 つの手法であり、目的となるモデルがデータの隠された (潜在的な) 構造を検出します。</span><span class="sxs-lookup"><span data-stu-id="f17a0-203">A subclass of machine learning in which a desired model finds hidden (or latent) structure in data.</span></span> <span data-ttu-id="f17a0-204">例として、クラスタリング、トピック モデリング、次元削減などがあります。</span><span class="sxs-lookup"><span data-stu-id="f17a0-204">Examples include clustering, topic modeling, and dimensionality reduction.</span></span> <span data-ttu-id="f17a0-205">詳しくは、Wikipedia の[教師なし学習](https://en.wikipedia.org/wiki/Unsupervised_learning)の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f17a0-205">For more information, see the [Unsupervised learning](https://en.wikipedia.org/wiki/Unsupervised_learning) article on Wikipedia.</span></span>

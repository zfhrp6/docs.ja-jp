---
title: 手書き認識
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d72d8b42a23205d8599b23a467677dd2f05d5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="handwriting-recognition"></a><span data-ttu-id="03b30-102">手書き認識</span><span class="sxs-lookup"><span data-stu-id="03b30-102">Handwriting Recognition</span></span>
<span data-ttu-id="03b30-103">このセクションでは、WPF プラットフォームのデジタル インクに関連する認識の基礎について説明します。</span><span class="sxs-lookup"><span data-stu-id="03b30-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="03b30-104">認識ソリューション</span><span class="sxs-lookup"><span data-stu-id="03b30-104">Recognition Solutions</span></span>  
 <span data-ttu-id="03b30-105">次の例は、[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) クラスを利用し、インクを認識する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="03b30-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03b30-106">このサンプルでは、手書き認識エンジンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03b30-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="03b30-107">Visual Studio で **InkRecognition** という名前の新しい WPF アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="03b30-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="03b30-108">Window1.xaml ファイルの内容を次の XAML コードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="03b30-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="03b30-109">このコードにより、アプリケーションのユーザー インターフェイスがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="03b30-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="03b30-110">Microsoft インク アセンブリである Microsoft.Ink.dll に参照を追加します。これは Program Files\Common Files\Microsoft Shared\Ink にあります。</span><span class="sxs-lookup"><span data-stu-id="03b30-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="03b30-111">この分離コード ファイルの内容を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="03b30-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="03b30-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="03b30-112">See Also</span></span>  
 <span data-ttu-id="03b30-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="03b30-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>

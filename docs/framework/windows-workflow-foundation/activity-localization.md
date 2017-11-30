---
title: "アクティビティのローカライズ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f7746e2ffc61db6d7863e243396f6d1bba315150
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="activity-localization"></a><span data-ttu-id="12e0a-102">アクティビティのローカライズ</span><span class="sxs-lookup"><span data-stu-id="12e0a-102">Activity Localization</span></span>
<span data-ttu-id="12e0a-103">ワークフロー アプリケーションとコンポーネントが他のカルチャおよび言語にローカライズされる可能性がある場合は、再コンパイルせずにローカライズできるようにリソース文字列を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e0a-103">When workflow applications and components have the potential to be localized into other cultures and languages, resource strings should be used so that they can be localized without recompiling.</span></span>  
  
## <a name="activity-localization"></a><span data-ttu-id="12e0a-104">アクティビティのローカライズ</span><span class="sxs-lookup"><span data-stu-id="12e0a-104">Activity Localization</span></span>  
 <span data-ttu-id="12e0a-105">ローカライズが必要なすべてのアプリケーション (言語とカルチャが異なり、異なるバージョンでリリースされたアプリケーション) について、ユーザーに表示される文字列は、コードに直接記述せず、リソース ファイルに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e0a-105">As with all applications that must be localized (released in different versions for different languages and cultures), any strings that are displayed to the user should not be put directly in code, but rather stored in a resource file.</span></span> <span data-ttu-id="12e0a-106">文字列を介してアクセス<!--zz <xref:System.Environment.GetResourceString> -->`GetResourceString`です。</span><span class="sxs-lookup"><span data-stu-id="12e0a-106">The strings can then be accessed through <!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`.</span></span> <span data-ttu-id="12e0a-107">複数の言語で配布されるコンポーネントを開発する場合、アクティビティの検証メッセージ、ユーザー定義の追跡データ、追跡メッセージ、およびエラー メッセージにもリソース文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="12e0a-107">If you are developing a component that is distributed in several languages, you also want to use resource strings for activity validation messages, user-defined tracking data, tracing messages, and error messages as well.</span></span>  
  
 <span data-ttu-id="12e0a-108">次の演習では、リソース ファイルの使用手順を示します。</span><span class="sxs-lookup"><span data-stu-id="12e0a-108">The following exercise demonstrates how to use a resource file.</span></span>  
  
#### <a name="using-resource-files-for-localized-strings"></a><span data-ttu-id="12e0a-109">ローカライズ文字列へのリソース ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="12e0a-109">Using resource files for localized strings</span></span>  
  
1.  <span data-ttu-id="12e0a-110">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)]でプロジェクトを右クリックして**ソリューション エクスプ ローラー**選択**追加しています.**、**新しい項目の追加**.</span><span class="sxs-lookup"><span data-stu-id="12e0a-110">In [!INCLUDE[vs2010](../../../includes/vs2010-md.md)], right-click your project in **Solution Explorer** and select **Add…**, **New Item…**.</span></span>  
  
2.  <span data-ttu-id="12e0a-111">選択**リソース ファイル**ErrorResources.resx というファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="12e0a-111">Select **Resources File** and name the file ErrorResources.resx.</span></span> <span data-ttu-id="12e0a-112">**[追加]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e0a-112">Click **Add**.</span></span>  
  
3.  <span data-ttu-id="12e0a-113">リソース ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="12e0a-113">Open the resource file.</span></span> <span data-ttu-id="12e0a-114">新しいエントリを追加、**名前**が ErrorString と**値**の「アクティビティが正しくありません」。</span><span class="sxs-lookup"><span data-stu-id="12e0a-114">Add a new entry with a **Name** of ErrorString and a **Value** of "The activity is not valid."</span></span>  
  
4.  <span data-ttu-id="12e0a-115">次の `using` ステートメントをクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="12e0a-115">Add the following `using` statements to your class.</span></span>  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  <span data-ttu-id="12e0a-116">プロジェクトでリソース マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="12e0a-116">Create a resource manager in your project.</span></span>  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  <span data-ttu-id="12e0a-117">必要に応じてリソース マネージャーから文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="12e0a-117">Get the string from the resource manager where it is required.</span></span>  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 <span data-ttu-id="12e0a-118">次のコードは、<xref:System.Activities.Activity.CacheMetadata%2A> メソッドでローカライズした文字列を利用する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="12e0a-118">The following code sample demonstrates how to utilize localized strings in the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span>  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```

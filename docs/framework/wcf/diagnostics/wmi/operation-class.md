---
title: "操作クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a><span data-ttu-id="9c42a-102">操作クラス</span><span class="sxs-lookup"><span data-stu-id="9c42a-102">Operation class</span></span>
<span data-ttu-id="9c42a-103">操作</span><span class="sxs-lookup"><span data-stu-id="9c42a-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c42a-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c42a-104">Syntax</span></span>  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9c42a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9c42a-105">Methods</span></span>  
 <span data-ttu-id="9c42a-106">Operation クラスで定義されているメソッドはありせん。</span><span class="sxs-lookup"><span data-stu-id="9c42a-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9c42a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9c42a-107">Properties</span></span>  
 <span data-ttu-id="9c42a-108">Operation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9c42a-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="9c42a-109">アクション</span><span class="sxs-lookup"><span data-stu-id="9c42a-109">Action</span></span>  
 <span data-ttu-id="9c42a-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="9c42a-110">Data type: string</span></span>  
  
 <span data-ttu-id="9c42a-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-112">要求メッセージの WS-Addressing 操作。</span><span class="sxs-lookup"><span data-stu-id="9c42a-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="9c42a-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="9c42a-113">AsyncPattern</span></span>  
 <span data-ttu-id="9c42a-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="9c42a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="9c42a-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-116">非同期的を使用して、操作を実装することを示す、 `Begin`[開く/閉じる山かっこ] と`End`サービス コントラクトで [開く/閉じる山かっこ] メソッドのペア。</span><span class="sxs-lookup"><span data-stu-id="9c42a-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="9c42a-117">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="9c42a-117">Behaviors</span></span>  
 <span data-ttu-id="9c42a-118">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="9c42a-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="9c42a-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-120">この操作に関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="9c42a-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="9c42a-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="9c42a-121">IsCallback</span></span>  
 <span data-ttu-id="9c42a-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="9c42a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="9c42a-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-124">この操作がコールバック操作の場合、True。</span><span class="sxs-lookup"><span data-stu-id="9c42a-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="9c42a-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="9c42a-125">IsInitiating</span></span>  
 <span data-ttu-id="9c42a-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="9c42a-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="9c42a-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-128">メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c42a-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="9c42a-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="9c42a-129">IsOneWay</span></span>  
 <span data-ttu-id="9c42a-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="9c42a-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="9c42a-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-132">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c42a-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="9c42a-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="9c42a-133">IsTerminating</span></span>  
 <span data-ttu-id="9c42a-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="9c42a-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="9c42a-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-136">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c42a-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="9c42a-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="9c42a-137">MethodSignature</span></span>  
 <span data-ttu-id="9c42a-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="9c42a-138">Data type: string</span></span>  
  
 <span data-ttu-id="9c42a-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-140">操作のメソッド署名。</span><span class="sxs-lookup"><span data-stu-id="9c42a-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9c42a-141">名前</span><span class="sxs-lookup"><span data-stu-id="9c42a-141">Name</span></span>  
 <span data-ttu-id="9c42a-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="9c42a-142">Data type: string</span></span>  
  
 <span data-ttu-id="9c42a-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-144">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="9c42a-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="9c42a-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="9c42a-145">ParameterTypes</span></span>  
 <span data-ttu-id="9c42a-146">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="9c42a-146">Data type: string array</span></span>  
  
 <span data-ttu-id="9c42a-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-148">操作のパラメーターの型。</span><span class="sxs-lookup"><span data-stu-id="9c42a-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="9c42a-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="9c42a-149">ReplyAction</span></span>  
 <span data-ttu-id="9c42a-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="9c42a-150">Data type: string</span></span>  
  
 <span data-ttu-id="9c42a-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-152">操作の応答メッセージの SOAP アクションの値。</span><span class="sxs-lookup"><span data-stu-id="9c42a-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="9c42a-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="9c42a-153">ReturnType</span></span>  
 <span data-ttu-id="9c42a-154">データ型: string</span><span class="sxs-lookup"><span data-stu-id="9c42a-154">Data type: string</span></span>  
  
 <span data-ttu-id="9c42a-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="9c42a-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9c42a-156">操作の戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="9c42a-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c42a-157">要件</span><span class="sxs-lookup"><span data-stu-id="9c42a-157">Requirements</span></span>  
  
|<span data-ttu-id="9c42a-158">MOF</span><span class="sxs-lookup"><span data-stu-id="9c42a-158">MOF</span></span>|<span data-ttu-id="9c42a-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="9c42a-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9c42a-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="9c42a-160">Namespace</span></span>|<span data-ttu-id="9c42a-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="9c42a-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c42a-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c42a-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>

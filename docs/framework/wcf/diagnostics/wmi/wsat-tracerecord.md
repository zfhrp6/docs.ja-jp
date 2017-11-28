---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="b5187-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b5187-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="b5187-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b5187-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5187-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5187-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b5187-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5187-105">Methods</span></span>  
 <span data-ttu-id="b5187-106">WSAT_TraceRecord クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="b5187-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b5187-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b5187-107">Properties</span></span>  
 <span data-ttu-id="b5187-108">WSAT_TraceRecord クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b5187-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="b5187-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="b5187-109">ActivityID</span></span>  
 <span data-ttu-id="b5187-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="b5187-110">Data type: object</span></span>  
<span data-ttu-id="b5187-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b5187-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5187-112">トレース レコードのアクティビティ ID です。</span><span class="sxs-lookup"><span data-stu-id="b5187-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="b5187-113">EventID</span><span class="sxs-lookup"><span data-stu-id="b5187-113">EventID</span></span>  
 <span data-ttu-id="b5187-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="b5187-114">Data type: sint32</span></span>  
<span data-ttu-id="b5187-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b5187-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5187-116">トレース レコードのイベント ID です。</span><span class="sxs-lookup"><span data-stu-id="b5187-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="b5187-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="b5187-117">TraceRecord</span></span>  
 <span data-ttu-id="b5187-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="b5187-118">Data type: string</span></span>  
<span data-ttu-id="b5187-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="b5187-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b5187-120">トレース レコード</span><span class="sxs-lookup"><span data-stu-id="b5187-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5187-121">要件</span><span class="sxs-lookup"><span data-stu-id="b5187-121">Requirements</span></span>  
  
|<span data-ttu-id="b5187-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b5187-122">MOF</span></span>|<span data-ttu-id="b5187-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="b5187-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b5187-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="b5187-124">Namespace</span></span>|<span data-ttu-id="b5187-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="b5187-125">Defined in root\ServiceModel</span></span>|

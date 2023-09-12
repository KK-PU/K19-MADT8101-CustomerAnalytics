# # Customer Analytics - work 05
 - Voice of Customer Analytics


## Import Dataset

  Data shows messages that were talked about in Social regarding the economy (Economy) in 2021.
  https://storage.googleapis.com/depa_social_data/aggregated/public/economy.csv


## Topic Modeling

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V5_VoiceOfCustomerAnalytics/processed_sentence.jpg)

**Configure Topic Modeling - LDA**

    num_topics = 500
    chunksize = 5000
    passes = 500
    iterations = 500
    eval_every = 5
    
    temp = dictionary[0]
    id2word = dictionary.id2token


**Displays the classification results of the LDA model in a 3D graph.**


![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V5_VoiceOfCustomerAnalytics/pyLDAvis.jpg)


## Document Clustering

**K-means clustering**

    wcss=[]
    max_k = 10
    for i in range(1, max_k):
        kmeans = KMeans(n_clusters=i, n_init='auto')
        kmeans.fit(umap_embed_comments_array)
        wcss_iter = kmeans.inertia_
        wcss.append(wcss_iter)
        number_clusters = range(1, max_k)
    
    plt.plot(number_clusters,wcss)
    plt.title('The Elbow title')
    plt.xlabel('Number of clusters')
    plt.ylabel('WCSS')
    

Cluster the data using K-Means clustering, with the number of possible clusters ranging from 1 to max_k - 1.

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V5_VoiceOfCustomerAnalytics/Elbow.jpg)

![Alt text](https://github.com/KK-PU/K19-MADT8101-CustomerAnalytics/blob/main/V5_VoiceOfCustomerAnalytics/df_kmeans.jpg)


Show top word of each clustere `3 Cluster ID` :

 - `cluster 0` :
   Most common words include : [('เงิน', 6), (';', 5), ('|', 4), ('&', 4), ('จีน', 4), ('quot', 4), ('หุ้น', 4), ('รัฐบาล', 3), ('ท่องเที่ยว', 3), ('คน', 3)]
   
 - `cluster 1` : Most common words include : [('|', 8), (';', 6), ('เงิน', 3), ('quot', 3), ('กรกฎาคม', 3), ('ดาว', 3), ('พุธ', 3), ('๔', 3), ('ติดต่อ', 3), ('สื่อสาร', 3)].
   
 - `cluster 2` : Most common words include : [('|', 10), ('สมัคร', 8), ('າ', 6), ('ร้าน', 4), ('່', 4), ('เด็ด', 3), ('อะเมซิ่ง', 3), ('ลือ', 3), ('EP#taiyang#jploy#', 3), ('เจพลอย', 3)]




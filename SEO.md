# SEO parts:

1. On Page SEO
2. Off Page SEO
3. Technical SEO

# On Page SEO

- its the important part of seo and its handled from the webpage its self
- **Examples:**

1. keywords research
2. competitor anayalize `تحليل المنافسين`
3. meta tags optimization
4. sitemap xml `خريطة الموقع`
5. optimize urls
6. internal links `الروابط الداخليه`
7. optimize images
8. robots.txt creation/anayalize
9. error page redirect
10. schema markup

# Technical SEO

- its also exist on web page like On Page SEO
- **Examples**

1. SiteMap HTML
2. site latency `هوية الموقع`
3. use ssl `حماية البيانات `
4. enabling amp `الصفحات المسرعة من غوغل`
5. user experience
6. website speed
7. page speed
8. resbonsive design
9. fix dublicate content `اصلاح المحتوى المكرر`

# Off Page SEO

- its handle the website from outside..
- **Examples:**

1. create backlinks `روابط خارجية عالية الجودة`
2. article marketing
3. social media

# KeyWords Research

- it is the words that user write it in google search engin to search what he want to see
- **Types of keywords**

1. long tail keyword `جملة مكونة من عدة كلمات والمنافسة عليها قليلة لأن اغلب المستخدمين بيكتبوا كلمات قصيرة`
2. short tail keyword `المنافسة عليها كبيرة لأنها تتكون من كلمتين على الاكثر`

- **How to Get some keywords for my website?**

1. we type some word in google and see what it does prupose for me...these are the keywords..
2. ahref keyword free generator website..

# Most common meta tags

1. title tag
2. `<meta name = "description" content = "" />`
3. `<meta name = "robots" content = "index" /> ` `//تخبر محركات البحث اذا كانت الصفحة قابلة للفهرسة او لا`
4. `<link rel="canonical" href = "" />` `//يمنع مشاكل المحتوى المكرر`
5. `<meta property = "og:title" content = "" />` `//تتحكم بشكل الرابط عند مشاركته في فيسبوك مثلا`

# How Search Engins works?

1. ### Crowling:

- robots visite the website and see tags and images ..etc

2. ### indexing

- after page is readed..google store it in big database

3. ### Ranking

- when user search in google .. it shows best ranked and most searched keyword results

# Http status code:

- 400 => bad request!(طلب غير صحيح)
- 401 => unAuthorized
- 403 => forbidden
- 404 => page not found
- 410 => page deleted finally
- 301 => page moved `used when url of page is changed!`
- 500 => server error or database error(backend error)

- 200 => proccess done successfully! with some data in response
- 201 => created successfully!
- 204 => request has been done but no response data has been sent..تم تنفيذ الطلب بس مافي بيانات مرسلة بالاستجابة وهذه ميزة سريعة

# Robots.txt

- it tells search engins what can it see in page
- Example

```
User-agent: * // it refers to all search engins
Disallow: /admin/ //dont come to /admin/
Allow: /public/ //it is allowed to /public
Sitemap: https://example.com/sitemap.xml //site map path
```

# SiteMap

- it is a map contains all important pages url's so google can easily index it

1. **XML sitemap:**

```
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://example.com/</loc>
    <lastmod>2025-11-10</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://example.com/courses</loc>
    <lastmod>2025-11-10</lastmod>
    <changefreq>weekly</changefreq>
    <priority>0.8</priority>
  </url>
</urlset>
```

# How to write seo in website?

```
            <Head>
                <title>{homeData?.seo_title}</title>
                <meta name="description" content={homeData?.meta_description} />
                <meta name="keywords" content={homeData?.keywords} />
                <meta name="og:title" content={homeData?.image_title} />
                <meta
                    name="og:description"
                    content={homeData?.meta_description}
                />
                <meta name="og:image" content={homeData?.image} />
                <meta name="og:image:alt" content={homeData?.image_alt} />
                <meta
                    name="og:image:caption"
                    content={homeData?.image_caption}
                />
                <meta
                    name="viewport"
                    content="width=device-width, initial-scale=1.0"
                />
            </Head>
```

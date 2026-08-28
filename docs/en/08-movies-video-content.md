# II.4 — Movies, Video & Creative content

> **EN** · [Français](../fr/08-movies-video-content.md)

## Movies (AMFMovieService)

| Action | Endpoint | Notes |
|--------|----------|-------|
| Save | SaveMovieWithSnapshot / CreateMovieWithSnapshot | movieId−1 = failure |
| Watch | MovieWatched | returnType 0/1/2 ; **awardedFame−429** |
| Rate | RateMovie | fame + SC possible |
| Publish | PublishMovie | |
| Favourites | AddActorFav / RemoveActorFav | AMFFavs mobile namespace |

## YouTube video (AMFVideoService)

Playlists, MSP TV, likes, views, reports, chat-room playback.

## Scrapblog (AMFScrapBlogService)

- SaveScrapBlogWithSnapshot
- LikeScrapBlog — **fameEarned−429**
- Feeds: newest, friends, highscore, search

## Photos (AMFImageUpload)

- UploadImageWithSnapshot — quota via GetRemainingUploadCount
- LikeImage — **Code−429**
- Codes −2 quota, −3 diamonds

## Design Studio

SaveDesignSecureWithSnapshot, SellDesign, BuyDesignCopy — design studio codes 0/−2 VIP/−3 SC/−4 diamonds.

## Detailed endpoints

→ [amf/08-movies.md](amf/08-movies.md) · [amf/09-video.md](amf/09-video.md) · [amf/12-content.md](amf/12-content.md)

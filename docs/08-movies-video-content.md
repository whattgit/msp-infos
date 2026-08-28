# II.4 — Films, Vidéo & Contenu créatif

## Films (AMFMovieService)

| Action | Endpoint | Notes |
|--------|----------|-------|
| Sauver | SaveMovieWithSnapshot / CreateMovieWithSnapshot | movieId−1 = échec |
| Visionner | MovieWatched | returnType 0/1/2 ; **awardedFame−429** |
| Noter | RateMovie | fame + SC possibles |
| Publier | PublishMovie | |
| Favoris | AddActorFav / RemoveActorFav | namespace AMFFavs mobile |

## Vidéo YouTube (AMFVideoService)

Playlists, MSP TV, likes, vues, signalements, lecture chat room.

## Scrapblog (AMFScrapBlogService)

- SaveScrapBlogWithSnapshot
- LikeScrapBlog — **fameEarned−429**
- Feeds : newest, friends, highscore, search

## Photos (AMFImageUpload)

- UploadImageWithSnapshot — quota via GetRemainingUploadCount
- LikeImage — **Code−429**
- Codes −2 quota, −3 diamants

## Design Studio

SaveDesignSecureWithSnapshot, SellDesign, BuyDesignCopy — codes design studio 0/−2 VIP/−3 SC/−4 diamants.

## Endpoints détaillés

→ [amf/08-movies.md](amf/08-movies.md) · [amf/09-video.md](amf/09-video.md) · [amf/12-content.md](amf/12-content.md)

Orphaned map function with surface type attribute naming convention
```javascript
const toUniqueCrlms = ({ id: cid, realms }) => {
    const realmList = realms.map(({ id, name, slug, timezone }) => ({
        id, nme: name, slug, tz: timezone
    }));
    let primary = realmList[0];

    return {
        id: cid,
        nme: primary.nme,
        slug: primary.slug,
        tz: primary.tz,
        rnm: realmList.map(({ nme }) => nme).join(', '),
        realms: realmList
    };
};
```
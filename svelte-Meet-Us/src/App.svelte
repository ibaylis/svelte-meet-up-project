<script>
    import Header from "./UI/Header.svelte";
    import MeetupGrid from "./Meetups/MeetupGrid.svelte";    


    let title = '';
    let subtitle = '';
    let address = '';
    let email = '';
    let description = '';
    let imageUrl = '';

    let meetups = [
        {
            id: 'm1',
            title: 'Coding Bootcamp',
            subtitle: "Learn to code in 2 hours",
            description: 'In this meetup, we will have some experts that teach you how to code',
            imageUrl: 'https://amp.businessinsider.com/images/5ada2bb619ee864e008b4634-1920-1440.jpg',
            address: '27th Nerd Road, New York City, New York, 14267',
            contactEmail: 'code@test.com'
        },
        {
        id: "m2",
        title: "Swim Together",
        subtitle: "Let's go for some swimming",
        description: "We will simply swim some rounds!",
        imageUrl:
            "https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Olympic_swimming_pool_%28Tbilisi%29.jpg/800px-Olympic_swimming_pool_%28Tbilisi%29.jpg",
        address: "27th Nerd Road, 32523 New York",
        contactEmail: "swim@test"
        }
    ];

const addMeetup = () => {
    const newMeetup = {
        id: Math.random().toString(),
        title: title,
        subtitle: subtitle,
        description: description,
        imageUrl: imageUrl,
        contactEmail: email,
        address: address
    }
    //DOES NOT WORK!!!
    // meetups.push(newMeetup);
    meetups = [newMeetup, ...meetups];

}

</script>

<style>
    main {
        margin-top: 5rem;
    }
</style>

<Header />

<main>
    <form on:submit|preventDefault="{addMeetup}">
        <div class="form-control">
            <label for="title">Title</label>
            <input type="text" id="title" bind:value={title} />
        </div>
        <div class="form-control">
            <label for="subtitle">Subtitle</label>
            <input type="text" id="subtitle" bind:value={subtitle} />
        </div>
        <div class="form-control">
            <label for="address">Address</label>
            <input type="text" id="address" bind:value={address} />
        </div>
        <div class="form-control">
            <label for="imageUrl">Image URL</label>
            <input type="text" id="imageUrl" bind:value={imageUrl} />
        </div>
        <div class="form-control">
            <label for="email">E-Mail</label>
            <input type="text" id="email" bind:value={email} />
        </div>
        <div class="form-control">
            <label for="description">Description</label>
            <textarea type="text" rows="3" id="description" bind:value={description}></textarea>
        </div>
        <button type="submit">Save</button>
    </form>
    <MeetupGrid {meetups} />
</main>







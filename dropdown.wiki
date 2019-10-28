

        <input class="dropdown_trigger_close"
               type="radio"
               name="bio_dropdown_trigger"
               id="bio_for_close"
               >


    <div>
        <div>
            <label for="for_uniq_name">open</label>
        </div>
        <input class="dropdown_trigger"
               type="radio"
               name="bio_dropdown_trigger"
               id="for_uniq_name"
               >
        <div class="dropdown">
            <label for="for_uniq_name">close</label>
        </div>
    </div>


    // dropdown mechanism
    .bio_dropdown_trigger,
    .bio_dropdown_trigger_close {
        display: none;
    }
    .dropdown {
        display: none;
    }
    .dropdown_trigger:checked + .dropdown {
        display: block;
    }
